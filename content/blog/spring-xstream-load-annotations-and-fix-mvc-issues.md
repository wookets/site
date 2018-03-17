+++
title = "Spring XStream Load Annotations and Fix MVC Issues"
date = 2011-05-02T14:51:00Z
updated = 2011-05-02T14:55:45Z
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

Wow. Covering the full gamut today. From Flex-Swiz-Event Order to Javascript-jQuery-Image Scaling to Java-Spring-Xml&nbsp;Marshalling.<br /><br />The problem I faced was this (<a href="http://forum.springsource.org/showthread.php?t=79963">http://forum.springsource.org/showthread.php?t=79963</a>). Essentially, Spring MVC / XStream sometimes maps a returned object (see below) to an&nbsp;incoherent&nbsp;string of framework object binding instructions.<br /><br />The Spring MVC Service<br /><br /><pre style="background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"><code style="color: black; word-wrap: normal;"> @Controller  <br /> public class SessionService {  <br />  @Autowired  <br />  private ServerSessionContext serverSessionContext;  <br />  @RequestMapping(value = "/validatesession")  <br />  public SessionValidationResponse validateSessionToken(@RequestParam String sessionToken) {  <br />   SessionValidationResponse response = new SessionValidationResponse();  <br />   response.isValid = serverSessionContext.doesSessionExist(sessionToken);  <br />   return response;  <br />  }  <br /> }  <br /></code></pre><br />The actual returned object is nothing more than a simple POJO.<br /><br /><pre style="background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"><code style="color: black; word-wrap: normal;"> package com.actifi.auth.dto;  <br /> import com.thoughtworks.xstream.annotations.XStreamAlias;  <br /> @XStreamAlias("sessionValidationResponse")  <br /> public class SessionValidationResponse {  <br />  public Boolean isValid = false;  <br /> }  <br /></code></pre><br />But, it would return some Binding....<br /><br /><pre  style="font-family:arial;font-size:12px;border:1px dashed #CCCCCC;width:99%;height:auto;overflow:auto;background:#f0f0f0;padding:0px;color:#000000;text-align:left;line-height:20px;"><code style="color:#000000;word-wrap:normal;"> &lt;org.springframework.validation.BeanPropertyBindingResult&gt;  <br /> &lt;nestedPath/&gt;  <br /> &lt;nestedPathStack serialization="custom"&gt;  <br /> &lt;unserializable-parents/&gt;  <br /> &lt;vector&gt;  <br /> &lt;default&gt;  <br /> &lt;capacityIncrement&gt;0&lt;/capacityIncrement&gt;  <br /> &lt;elementCount&gt;0&lt;/elementCount&gt;  <br /> thousands of lines omitted for brevity  <br /></code></pre><br /><br />The solution for fixing the problem is in the two reference links below. And... as they recommend... they want you to actually type class full names (package and all) into the spring config file. I like the way my current spring xml config looks...<br /><br /><pre style="background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"><code style="color: black; word-wrap: normal;">  &lt;!-- oxm integration --&gt;  <br />  &lt;bean id="objectXmlMarshaller" class="org.springframework.oxm.xstream.XStreamMarshaller"/&gt;  <br /></code></pre><br />So... here is a bootstrapper class and a scan class util to make things 'automagic'.<br /><br />Generic scan helper class (requires spring framework)<br /><br /><pre style="background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"><code style="color: black; word-wrap: normal;"> package com.wookets.bootstrap;  <br /> import java.util.ArrayList;  <br /> import java.util.List;  <br /> import org.springframework.beans.factory.config.BeanDefinition;  <br /> import org.springframework.context.annotation.ClassPathScanningCandidateComponentProvider;  <br /> import org.springframework.util.ClassUtils;  <br /> /**  <br />  * This will scan the classpath for certain classes that you may want to register based on annotations  <br />  * or something similar... This uses ASM and spring stuff, so we know it is good.  <br />  *  <br />  * usage  <br />  *  <br />  *  final ComponentClassScanner scanner = new ComponentClassScanner();  <br />  *  scanner.addIncludeFilter(new AnnotationTypeFilter(DbRevision.class));  <br />  *  final List&lt;Class&lt;? extends Object&gt;&gt; classes = scanner.getComponentClasses(this.CLASS_PATH);  <br />  *  <br />  * @author wookets  <br />  *  <br />  */  <br /> public class ComponentClassScanner extends ClassPathScanningCandidateComponentProvider {  <br />  public ComponentClassScanner() {  <br />   super(false);  <br />  }  <br />  public final List&lt;Class&lt;? extends Object&gt;&gt; getComponentClasses(String basePackage) {  <br />   basePackage = basePackage == null ? "" : basePackage;  <br />   final List&lt;Class&lt;? extends Object&gt;&gt; classes = new ArrayList&lt;Class&lt;? extends Object&gt;&gt;();  <br />   for(final BeanDefinition candidate : this.findCandidateComponents(basePackage)) {  <br />    try {  <br />     final Class&lt;? extends Object&gt; cls = ClassUtils.resolveClassName(candidate.getBeanClassName(), ClassUtils.getDefaultClassLoader());  <br />     classes.add(cls);  <br />    } catch (final Throwable ex) {  <br />     ex.printStackTrace();  <br />    }  <br />   }  <br />   return classes;  <br />  }  <br /> }  <br /></code></pre><br />xstream xml bootstrapper. This will read in annotations and add classes to the supported classes property to avoid the above issues with binding bean things. <br /><br /><pre style="background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"><code style="color: black; word-wrap: normal;"> package com.wookets.bootstrap;  <br /> import java.util.List;  <br /> import org.springframework.beans.factory.annotation.Autowired;  <br /> import org.springframework.context.ApplicationEvent;  <br /> import org.springframework.context.ApplicationListener;  <br /> import org.springframework.context.event.ContextRefreshedEvent;  <br /> import org.springframework.core.type.filter.AnnotationTypeFilter;  <br /> import org.springframework.oxm.xstream.XStreamMarshaller;  <br /> import org.springframework.stereotype.Component;  <br /> import com.thoughtworks.xstream.annotations.XStreamAlias;  <br /> /**  <br />  * This will alias the xml types with the xml marsheller, so we can use annotations on our xml types and do all aliasing  <br />  * and caching up front.  <br />  *   <br />  * @author wookets  <br />  *   <br />  */  <br /> @SuppressWarnings("rawtypes")  <br /> @Component  <br /> public class ServerStartupAliasXmlType implements ApplicationListener {  <br />  private boolean hasBeenCreated = false;  <br />  @Autowired  <br />  private XStreamMarshaller objectXmlMarshaller;  <br />  @Override  <br />  public void onApplicationEvent(ApplicationEvent event) {  <br />   if(this.hasBeenCreated)  <br />    return;  <br />   if(event instanceof ContextRefreshedEvent) {  <br />    this.hasBeenCreated = true;  <br />    final ComponentClassScanner scanner = new ComponentClassScanner();  <br />    scanner.addIncludeFilter(new AnnotationTypeFilter(XStreamAlias.class));  <br />    final List&lt;Class&lt;?&gt;&gt; classes = scanner.getComponentClasses("com.wookets");  <br />    for(final Class&lt;?&gt; c : classes) {  <br />     this.objectXmlMarshaller.getXStream().processAnnotations(c);  <br />    }  <br />    this.objectXmlMarshaller.setSupportedClasses(classes.toArray(new Class[0]));  <br />   }  <br />  }  <br />  public void setObjectXmlMarshaller(XStreamMarshaller objectXmlMarshaller) {  <br />   this.objectXmlMarshaller = objectXmlMarshaller;  <br />  }  <br /> }  <br /></code></pre><br />I think I had more to add, but... oh yeah... A link to some files to download...<br /><br /><a href="http://wookets.com/code/java/SpringBootstrap/">http://wookets.com/code/java/SpringBootstrap/</a><br /><br />References:<br /><br /><a href="http://forum.springsource.org/showthread.php?t=97048">http://forum.springsource.org/showthread.php?t=97048</a><br /><br /><a href="http://forum.springsource.org/showthread.php?t=79963">http://forum.springsource.org/showthread.php?t=79963</a>
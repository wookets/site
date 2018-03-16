+++
title = "Spring AOP Method Profiler"
date = 2011-12-03T22:14:00Z
updated = 2011-12-03T22:17:50Z
tags = ["Code"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

This is a poor man's application profiler. Note, that this profiler is going to be limited, since it is running inside the application, but also nice that it is running inside the application. Anyway, I find it helpful to measure individual service calls against other service calls. One could even add a limit into this method, if it takes longer than x, send me an email because something is wrong... Though, I'm pretty sure this code is not to great for production builds.<br /><br />Enough babble;<br /><br /><br /><pre class="brush:java">import org.aspectj.lang.ProceedingJoinPoint;<br />import org.aspectj.lang.annotation.After;<br />import org.aspectj.lang.annotation.Around;<br />import org.aspectj.lang.annotation.Aspect;<br />import org.slf4j.Logger;<br />import org.slf4j.LoggerFactory;<br />import org.springframework.stereotype.Component;<br /><br />@Component<br />@Aspect<br />public class TimeExecutionProfiler {<br />  private static final Logger log = LoggerFactory.getLogger(TimeExecutionProfiler.class);<br /><br />  @Around("SystemArchitecture.serviceOperation()")<br />  public Object profile(ProceedingJoinPoint pjp) throws Throwable {<br />    long start = System.currentTimeMillis();<br />    Object output = pjp.proceed();<br />    long elapsedTime = System.currentTimeMillis() - start;<br />    log.info("ServicesProfiler.profile(): Method execution time: " + elapsedTime + " milliseconds.");<br />    return output;<br />  }<br /><br />  @After("SystemArchitecture.serviceOperation()")<br />  public void profileMemory() {<br />    log.info("JVM memory in use = "<br />        + ((Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory()) / 1048576) + " MB");<br />  }<br />}<br /><br /></pre>

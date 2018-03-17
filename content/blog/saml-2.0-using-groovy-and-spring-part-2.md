+++
title = "SAML 2.0 using Groovy and Spring (part 2)"
date = 2011-11-22T21:29:00Z
updated = 2011-11-22T21:37:16Z
tags = ["Code"]
blogimport = true 
[author]
	name = "Sean Wesenberg"
	uri = "https://plus.google.com/111523202047342274226"
+++

In <a href="http://blog.wookets.com/2011/11/saml-20-using-groovy-and-spring.html">part 1</a>, I showed you how to write a Controller and a Service which creates the AuthnRequest and sends a redirect.<br /><br />I should mention that Controller is entirely derived from Spring's MVC use of the word, but we in fact are not using it to handle or communicate with a view, just for the amazingly simple HTTP servlet like features.<br /><br />Now, in part 2, we will add to the Controller and Service classes methods which make handling the incoming SAML Assertion HTTP POST cake.<br /><br />Added to our SAMLController.groovy<br /><br /><pre class="brush:java">  <br />  @RequestMapping(value = "/sso/saml2/verifyassertion")<br />  def verifySamlAssertion(HttpServletResponse response, @RequestParam String SAMLResponse) {<br />    log.debug "Incoming SAMLResponse: \n ${SAMLResponse}"<br />    <br />    def decodedResponse = new String(SAMLResponse.decodeBase64())<br />    log.debug "Decoded response: ${decodedResponse}"<br />    // call our service with the decoded message<br />    samlService.verifyAssertion(SAMLResponse: decodedResponse)<br />    <br />    // an exception will be thrown if we don't reach this point<br />    response.writer.write("success")<br />  }<br /></pre><br />Added to our SAMLService.groovy<br /><br /><br /><pre class="brush:java">  def verifyAssertion = {<br />    String samlResponse = Param.notEmpty it, "SAMLResponse" // this is just a helper method to check incoming params<br />    <br />    log.debug "Parsing incoming SAMLResponse ${samlResponse}"<br />    // parse incoming response<br />    def xml = new XmlSlurper().parseText(samlResponse)<br />    xml.declareNamespace(samlp: "urn:oasis:names:tc:SAML:2.0:protocol", saml: 'urn:oasis:names:tc:SAML:2.0:assertion',<br />                         ds: "http://www.w3.org/2000/09/xmldsig#")<br />    <br />    // validate issuer<br />    def issuer = xml.'saml:Issuer'.text()<br />    log.debug "Issuer: ${issuer}"<br /><br />    // validate status code is success<br />    def statusCode = xml.'samlp:Status'.'samlp:StatusCode'.@Value.text()<br />    log.debug "StatusCode: ${statusCode}"<br />    <br />    // validate within time<br />    <br />    // validate signature<br />    <br />    // validate cert<br />    def cert = xml.'saml:Assertion'.'ds:Signature'.'ds:KeyInfo'.'ds:X509Data'.'ds:X509Certificate'.text()<br />    log.debug "Cert: ${cert}"<br />    <br />    // make sure request hasn't expired from the db<br />    <br />    // validate the original requestId<br />    def requestId = xml.@'InResponseTo'.text()<br />    log.debug "Original requestId: ${requestId}"<br />      <br />    // look up the user in our system and create a session id (ie sign them in)<br />    def username = xml.'saml:Assertion'.'saml:Subject'.'saml:NameID'.text()<br />    log.debug "looking up the user in our system to verify that they exist and have a username matching ${username}"<br />    <br />    log.debug "finished asserting: success" // if we reached this point, we passed the saml test<br />  }<br /></pre><br />Pretty straightforward (if you know Groovy, Spring MVC) and better we added no&nbsp;extraneous&nbsp;jars to our project.<br /><br />
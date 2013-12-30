
.. code-block:: bash

 curl -s --user 'api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0' -X DELETE \
     https://api.mailgun.net/v2/domains/samples.mailgun.org/webhooks/click

.. code-block:: java

 public static ClientResponse DeleteDomain() {
 	Client client = Client.create();
 	client.addFilter(new HTTPBasicAuthFilter("api",
 			"key-3ax6xnjp29jd6fds4gc373sgvjxteol0"));
 	WebResource webResource =
 		client.resource("https://api.mailgun.net/v2" +
 				"/domains/samples.mailgun.org/webhooks/click");
 	return webResource.delete(ClientResponse.class);
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('key-3ax6xnjp29jd6fds4gc373sgvjxteol0');
  $domain = 'samples.mailgun.org';

  # Issue the call to the client.
  $result = $mgClient->delete("$domain/webhooks/click");

.. code-block:: py

 def delete_domain():
     return requests.delete(
         "https://api.mailgun.net/v2/domains/samples.mailgun.org/webhooks/click",
         auth=("api", "key-3ax6xnjp29jd6fds4gc373sgvjxteol0"))

.. code-block:: rb

 def delete_domain
   RestClient.delete "https://api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0"\
   "@api.mailgun.net/v2/domains/samples.mailgun.org/webhooks/click"
 end

.. code-block:: csharp

 public static IRestResponse DeleteDomain() {
 	RestClient client = new RestClient();
 	client.BaseUrl = "https://api.mailgun.net/v2";
 	client.Authenticator =
 		new HttpBasicAuthenticator("api",
 		                           "key-3ax6xnjp29jd6fds4gc373sgvjxteol0");
 	RestRequest request = new RestRequest();
 	request.Resource = "/domains/{name}/webhooks/click";
 	request.AddUrlSegment("name", "samples.mailgun.org");
 	request.Method = Method.DELETE;
 	return client.Execute(request);
 }

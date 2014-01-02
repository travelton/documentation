
.. code-block:: bash

  curl -s --user 'api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0' -G \
    https://api.mailgun.net/v2/ips/184.173.153.199

.. code-block:: java

 public static ClientResponse GetIP() {
 	Client client = new Client();
 	client.addFilter(new HTTPBasicAuthFilter("api",
 			"key-3ax6xnjp29jd6fds4gc373sgvjxteol0"));
 	WebResource webResource =
 		client.resource("https://api.mailgun.net/v2/ips/184.173.153.199);
 	return webResource.get(ClientResponse.class);
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('key-3ax6xnjp29jd6fds4gc373sgvjxteol0');
  
  # Issue the call to the client.
  $result = $mgClient->get("ips/184.173.153.199");

.. code-block:: py

 def get_ip():
     return requests.get(
         "https://api.mailgun.net/v2/ips/184.173.153.199",
         auth=("api", "key-3ax6xnjp29jd6fds4gc373sgvjxteol0"))

.. code-block:: rb

 def get_ip
   RestClient.get("https://api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0"\
                  "@api.mailgun.net/v2/ips/184.173.153.199"\
                  {|response, request, result| response }
 end

.. code-block:: csharp

 public static IRestResponse GetIP() {
 	RestClient client = new RestClient();
 	client.BaseUrl = "https://api.mailgun.net/v2";
 	client.Authenticator =
 		new HttpBasicAuthenticator("api",
 		                           "key-3ax6xnjp29jd6fds4gc373sgvjxteol0");
 	RestRequest request = new RestRequest();
       request.Resource = "ips/184.173.153.199";
 	return client.Execute(request);
 }

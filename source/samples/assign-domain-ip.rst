
.. code-block:: bash

    curl -s --user 'api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0' \
	https://api.mailgun.net/v2/domains/samples.mailgun.org/184.173.153.199

.. code-block:: java

 public static ClientResponse AssignIP() {
 	Client client = new Client();
 	client.addFilter(new HTTPBasicAuthFilter("api",
 			"key-3ax6xnjp29jd6fds4gc373sgvjxteol0"));
 	WebResource webResource =
 		client.resource("https://api.mailgun.net/v2/domains/" +
                    "samples.mailgun.org/184.173.153.199");
 	return webResource.type(MediaType.APPLICATION_FORM_URLENCODED).
 	post(ClientResponse.class);
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('key-3ax6xnjp29jd6fds4gc373sgvjxteol0');
  $domain = 'samples.mailgun.org';
  $ip = '184.173.153.199';

  # Issue the call to the client.
   $result = $mgClient->post("domains/$domain/$ip");

.. code-block:: py

 def assign_ip():
     return requests.post(
         "https://api.mailgun.net/v2/domains/samples.mailgun.org/184.173.153.199",
         auth=("api", "key-3ax6xnjp29jd6fds4gc373sgvjxteol0"))

.. code-block:: rb

 def assign_ip
   RestClient.post("https://api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0"\
                   "@api.mailgun.net/v2/domains/samples.mailgun.org/184.173.153.199")
 end

.. code-block:: csharp

  public static IRestResponse AssignIP() {
    RestClient client = new RestClient();
    client.BaseUrl = "https://api.mailgun.net/v2/";
    client.Authenticator =
      new HttpBasicAuthenticator("api",
                                 "key-3ax6xnjp29jd6fds4gc373sgvjxteol0");
    RestRequest request = new RestRequest();
    request.Resource = "domains/{domain}/{ip}";
    request.AddUrlSegment("domain", "example.mailgun.org");
    request.AddUrlSegment("ip", "184.173.153.199");
    request.Method = Method.POST;
    return client.Execute(request);
  }


.. code-block:: bash

 curl -s --user 'api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0' -X DELETE \
     https://api.mailgun.net/v2/domains/example.mailgun.org/184.173.153.199

.. code-block:: java

 public static ClientResponse UnassignIP() {
 	Client client = Client.create();
 	client.addFilter(new HTTPBasicAuthFilter("api",
 			"key-3ax6xnjp29jd6fds4gc373sgvjxteol0"));
 	WebResource webResource =
 		client.resource("https://api.mailgun.net/v2" +
 				"/domains/example.mailgun.org/184.173.153.199");
 	return webResource.delete(ClientResponse.class);
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('key-3ax6xnjp29jd6fds4gc373sgvjxteol0');
  $domain = 'example.mailgun.org';
  $ip = '184.173.153.199'

  # Issue the call to the client.
  $result = $mgClient->delete("domains/$domain/$ip");

.. code-block:: py

 def unassign_ip():
     return requests.delete(
         "https://api.mailgun.net/v2/domains/example.mailgun.org/184.173.153.199",
         auth=("api", "key-3ax6xnjp29jd6fds4gc373sgvjxteol0"))

.. code-block:: rb

  def unassign_ip
    RestClient.delete "https://api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0"\
    "@api.mailgun.net/v2/domains/example.mailgun.org/184.173.153.199"
  end

.. code-block:: csharp

  public static IRestResponse UnassignIP() {
    RestClient client = new RestClient();
    client.BaseUrl = "https://api.mailgun.net/v2";
    client.Authenticator =
      new HttpBasicAuthenticator("api",
                                 "key-3ax6xnjp29jd6fds4gc373sgvjxteol0");
    RestRequest request = new RestRequest();
    request.Resource = "/domains/{domain}/{ip}";
    request.AddUrlSegment("domain", "example.mailgun.org");
    request.AddUrlSegment("ip", "184.173.153.199");
    request.Method = Method.DELETE;
    return client.Execute(request);
  }

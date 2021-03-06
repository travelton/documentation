
.. code-block:: bash

    curl -s --user 'api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0' -G \
      https://api.mailgun.net/v2/samples.mailgun.org/bounces \
        -d skip=1 \
        -d limit=1

.. code-block:: java

 public static ClientResponse GetBounces() {
  Client client = new Client();
  client.addFilter(new HTTPBasicAuthFilter("api",
      "key-3ax6xnjp29jd6fds4gc373sgvjxteol0"));
  WebResource webResource =
    client.resource("https://api.mailgun.net/v2/samples.mailgun.org" +
        "/bounces");
  return webResource.get(ClientResponse.class);
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('key-3ax6xnjp29jd6fds4gc373sgvjxteol0');
  $domain = 'samples.mailgun.org';

  # Issue the call to the client.
  $result = $mgClient->get("$domain/bounces", array('skip' => 0, 'limit' => 50));

.. code-block:: py

 def get_bounces():
     return requests.get(
         "https://api.mailgun.net/v2/samples.mailgun.org/bounces",
         auth=("api", "key-3ax6xnjp29jd6fds4gc373sgvjxteol0"))

.. code-block:: rb

 def get_bounces
   RestClient.get "https://api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0"\
   "@api.mailgun.net/v2/samples.mailgun.org/bounces"
 end

.. code-block:: csharp

 public static IRestResponse GetBounces() {
  RestClient client = new RestClient();
  client.BaseUrl = "https://api.mailgun.net/v2";
  client.Authenticator =
    new HttpBasicAuthenticator("api",
                               "key-3ax6xnjp29jd6fds4gc373sgvjxteol0");
  RestRequest request = new RestRequest();
  request.AddParameter("domain",
                       "samples.mailgun.org", ParameterType.UrlSegment);
  request.Resource = "{domain}/bounces";
  return client.Execute(request);
 }

.. code-block:: go

 func GetBounces(domain, apiKey string) (int, []mailgun.Bounce, error) {
   mg := mailgun.NewMailgun(domain, apiKey, "")
   total, bounces, err := mg.GetBounces(-1, -1)
   return total, bounces, err
 }

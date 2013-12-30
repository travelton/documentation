
.. code-block:: bash

    curl -s --user 'api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0' \
	https://api.mailgun.net/v2/samples.mailgun.org/unsubscribes \
	-F address='bob@example.com' \
	-F tag='*'

.. code-block:: java

 public static ClientResponse UnsubscribeFromAll() {
 	Client client = new Client();
 	client.addFilter(new HTTPBasicAuthFilter("api",
 			"key-3ax6xnjp29jd6fds4gc373sgvjxteol0"));
 	WebResource webResource =
 		client.resource("https://api.mailgun.net/v2/samples.mailgun.org" +
 				"/unsubscribes");
 	MultivaluedMapImpl formData = new MultivaluedMapImpl();
 	formData.add("address", "bob@example.com");
 	formData.add("tag", "*");
 	return webResource.type(MediaType.APPLICATION_FORM_URLENCODED).
 		post(ClientResponse.class, formData);
 }

.. code-block:: php

  # Include the Autoloader (see "Libraries" for install instructions)
  require 'vendor/autoload.php';
  use Mailgun\Mailgun;

  # Instantiate the client.
  $mgClient = new Mailgun('key-3ax6xnjp29jd6fds4gc373sgvjxteol0');
  $domain = 'samples.mailgun.org';

  # Issue the call to the client.
  $result = $mgClient->post("$domain/unsubscribes", 
                            array('address' => 'bob@example.com', 'tag' => '*'));

.. code-block:: py

 def unsubscribe_from_all():
     return requests.post(
         "https://api.mailgun.net/v2/samples.mailgun.org/unsubscribes",
         auth=("api", "key-3ax6xnjp29jd6fds4gc373sgvjxteol0"),
         data={'address':'bob@example.com', 'tag': '*'})

.. code-block:: rb

 def unsubscribe_from_all
   RestClient.post "https://api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0"\
   "@api.mailgun.net/v2/samples.mailgun.org/unsubscribes",
   :address => 'bob@example.com',
   :tag => '*'
 end

.. code-block:: csharp

 public static IRestResponse UnsubscribeFromAll() {
 	RestClient client = new RestClient();
 	client.BaseUrl = "https://api.mailgun.net/v2";
 	client.Authenticator =
 		new HttpBasicAuthenticator("api",
 		                           "key-3ax6xnjp29jd6fds4gc373sgvjxteol0");
 	RestRequest request = new RestRequest();
 	request.Resource = "{domain}/unsubscribes";
 	request.AddParameter("domain",
 	                     "samples.mailgun.org", ParameterType.UrlSegment);
 	request.AddParameter("address", "bob@example.com");
 	request.AddParameter("tag", "*");
 	request.Method = Method.POST;
 	return client.Execute(request);
 }

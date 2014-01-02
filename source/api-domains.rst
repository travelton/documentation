.. _api-domains:

Domains
=======

This API allows you to create, access, and validate domains programmatically.

.. code-block:: url

     GET /domains

Returns a list of domains under your account in JSON. See examples below.

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 limit             Maximum number of records to return. (100 by default)
 skip              Number of records to skip. (0 by default)
 ================= ========================================================

.. code-block:: url

     GET /domains/<domain>

Returns a single domain, including credentials and DNS records. See examples below.

.. code-block:: url

     GET /domains/<domain>/ips

Returns a list of IPs currently assigned to the specified domain.

.. code-block:: url

     POST /domains

Create a new domain. See examples below.

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 name              Name of the domain (ex. domain.com)
 smtp_password     Password for SMTP authentication
 spam_action       *disabled* or *tag* Disable, no spam filtering will occur
                   for inbound messages. Tag, messages will be tagged wtih a
                   spam header. See :ref:`um-spam-filter`.
 wildcard          *true* or *false* Determines whether the domain will
                   accept email for sub-domains.
 ================= ========================================================

.. code-block:: url

     POST /domains/<domain>/<ip>

Assign an IP to the domain specified.

.. note:: Please see the IP Management API to obtain a list of available IPs for your account. 

.. code-block:: url

     DELETE /domains/<domain>

Delete a domain from your account.

.. code-block:: url

     DELETE /domains/<domain>/<ip>

Unassign an IP from the domain specified.

.. warning:: A domain must have at least one IP assigned. A 400 error will be thrown if you attempt to remove the last IP from a domain.  

.. note:: Mailgun imposes a rate limit for the Domains API endpoint. Users may 
		  issue no more than 300 requests per minute, per account. See the resultant
		  rate limit response below. 

Example
~~~~~~~

Get a list of all domains.

.. include:: samples/get-domains.rst

Sample response:

.. code-block:: javascript

	{
	  "total_count": 1,
	  "items": [
	    {
	      "created_at": "Wed, 10 Jul 2013 19:26:52 GMT",
	      "smtp_login": "postmaster@samples.mailgun.org",
	      "name": "samples.mailgun.org",
	      "smtp_password": "4rtqo4p6rrx9",
	      "wildcard": true, 
	      "spam_action": "disabled"
	    }
	  ]
	}

Possible response codes:

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 200               Request successful
 500               Internal Server Error
 ================= ========================================================

Get a single domain.

.. include:: samples/get-domain.rst

Sample response:

.. code-block:: javascript

	{
	  "domain": {
	    "created_at": "Wed, 10 Jul 2013 19:26:52 GMT",
	    "smtp_login": "postmaster@domain.com",
	    "name": "domain.com",
	    "smtp_password": "4rtqo4p6rrx9",
	    "wildcard": false, 
	    "spam_action": "tag"
	  },
	  "receiving_dns_records": [
	    {
	      "priority": "10",
	      "record_type": "MX",
	      "valid": "valid",
	      "value": "mxa.mailgun.org"
	    },
	    {
	      "priority": "10",
	      "record_type": "MX",
	      "valid": "valid",
	      "value": "mxb.mailgun.org"
	    }
	  ],
	  "sending_dns_records": [
	    {
	      "record_type": "TXT",
	      "valid": "valid",
	      "name": "domain.com",
	      "value": "v=spf1 include:mailgun.org ~all"
	    },
	    {
	      "record_type": "TXT",
	      "valid": "valid",
	      "name": "domain.com",
	      "value": "k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUA...."
	    },
	    {
	      "record_type": "CNAME",
	      "valid": "valid",
	      "name": "email.domain.com",
	      "value": "mailgun.org"
	    }
	  ]
	}

Possible response codes:

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 200               Request successful
 404               Domain not found for account
 500               Internal Server Error
 ================= ========================================================

Adding a domain.

.. include:: samples/add-domain.rst

Sample response:

.. code-block:: javascript

	{
	  "domain": {
	    "name": "example.com", 
	    "created_at": "Fri, 22 Nov 2013 18:42:33 GMT", 
	    "wildcard": false, 
	    "spam_action": "disabled", 
	    "smtp_login": "postmaster@example.com", 
	    "smtp_password": "thiswontwork"
	  }, 
	  "receiving_dns_records": [
	    {
	      "priority": "10", 
	      "record_type": "MX", 
	      "valid": "valid", 
	      "value": "mxa.mailgun.org"
	    }, 
	    {
	      "priority": "10", 
	      "record_type": "MX", 
	      "valid": "valid", 
	      "value": "mxb.mailgun.org"
	    }
	  ], 
	  "message": "Domain has been created", 
	  "sending_dns_records": [
	    {
	      "record_type": "TXT", 
	      "valid": "valid", 
	      "name": "example.com", 
	      "value": "v=spf1 include:mailgun.org ~all"
	    }, 
	    {
	      "record_type": "TXT", 
	      "valid": "valid", 
	      "name": "k1._domainkey.example.com", 
	      "value": "k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4G...."
	    }, 
	    {
	      "record_type": "CNAME", 
	      "valid": "valid", 
	      "name": "email.example.com", 
	      "value": "mailgun.org"
	    }
	  ]
	}

Possible response codes:

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 200               Request successful
 400               Domain already exists within system
 500               Internal Server Error
 ================= ========================================================	

Deleting a domain.

.. include:: samples/delete-domain.rst

Sample response:

.. code-block:: javascript

	{
	  "message": "Domain has been deleted"
	}

Possible response codes:

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 200               Request successful
 404               Domain not found for account
 500               Internal Server Error
 ================= ========================================================	

List all IPs for a domain.

.. include:: samples/list-domain-ips.rst

Sample response:

.. code-block:: javascript

	{
	    "total_count": 2,
	    "items": [
	        "184.173.153.199",
	        "127.0.0.2"
	    ]
	}

Possible response codes:

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 200               Request successful
 404               Domain not found for account
 500               Internal Server Error
 ================= ========================================================	

Assign an IP to a domain.

.. include:: samples/assign-domain-ip.rst

Sample response:

.. code-block:: javascript

	{
	    "message": "IP successfully assigned to domain",
	    "ip": "184.173.153.199"
	}

Possible response codes:

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 200               Request successful
 400               Not a valid IP address
 404               Domain or IP not found for account
 500               Internal Server Error
 ================= ========================================================	

Unassign an IP from a domain.

.. include:: samples/unassign-domain-ip.rst

Sample response:

.. code-block:: javascript

	{
	    "message": "IP successfully unassigned from domain",
	    "ip": "184.173.153.199"
	}

Possible response codes:

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 200               Request successful
 400               Not a valid IP address
 404               Domain or IP not found for account
 500               Internal Server Error
 ================= ========================================================	

Rate Limit Response:

.. code-block:: javascript

	{
	  "retry-seconds": 60,
	}

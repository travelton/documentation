.. _api-ips:

IPs
===

The IP API endpoint allows you to access information regarding IPs, allocated to
your Mailgun account, used for outbound sending.

For all new accounts, a single shared IP will be automatically allocated to your account. Through your Mailgun Control Panel, you may upgrade your account to add a dedicated IP address, for an additional monthly fee. 

Outbound sending speed involves many factors, one being the amount of IPs assigned to the sending domain. If you are experiencing slow sending speeds, and sending speed is important, please contact our support team for guidance. Our sending experts will review your account and determine if additional IPs will help. 

For more information regarding IPs, Sending Volume, and Reputation, see our :ref:`best-practices` guide. 

.. code-block:: url

     GET /ips

Returns a list of IP addresses allocated to your account in JSON. See examples below.

.. code-block:: url

     GET /ips/<ip>

Returns a single IP, including information related to that IP. See examples below.

.. code-block:: url

     GET /ips/<ip>/domains

Returns a list of domains currently assigned to the specified IP address.

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 limit             Maximum number of records to return. (100 by default)
 skip              Number of records to skip. (0 by default)
 ================= ========================================================


Example
~~~~~~~

Retrieve a list of IPs currently allocated to your account.

.. include:: samples/get-ips.rst

Sample response:

.. code-block:: javascript

  {
    "total_count": 3, 
    "items": [
      "210.91.10.5", 
      "190.16.1.104", 
      "190.16.1.106"
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

Retrieve details related to a single IP.

.. include:: samples/get-ip.rst

Sample response:

.. code-block:: javascript

  {
    "ip": "210.91.10.5", 
    "dedicated": false, 
    "rdns": null
  }

Possible response codes:

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 200               Request successful
 400               Not a valid IP address
 404               IP address not found for account
 500               Internal Server Error
 ================= ========================================================

Retrieve all domains currently assigned to a specified IP.

.. include:: samples/get-ip-domains.rst

Sample response:

.. code-block:: javascript

  {
    "total_count": 2, 
    "items": [
      {
        "ips": [
          "210.91.10.5"
        ], 
        "domain": "testing.mailgun.org"
      }, 
    {
      "ips": [
        "210.91.10.5", 
        "190.16.1.104"
      ], 
      "domain": "example.com"
      }
    ]
  }

Possible response codes:

.. container:: ptable

 ================= ========================================================
 Parameter         Description
 ================= ========================================================
 200               Request successful
 400               Not a valid IP address
 404               IP address not found for account
 500               Internal Server Error
 ================= ========================================================

Rate Limit Response:

.. code-block:: javascript

  {
    "retry-seconds": 60,
  }

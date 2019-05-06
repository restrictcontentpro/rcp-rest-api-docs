# Customers

The customers route allows you to interact with the Restrict Content Pro customers database to retrieve customers, add new ones, update existing customers, and delete customers.

<aside class="notice">
	Note: This endpoint is only available if you have Restrict Content Pro version 3.0 or higher installed.
</aside>

## Customer object

| Attribute | Type | Description |
| --------- | ---- | ----------- |
| `id`      | integer | Unique identifier for the object. |
| `user_id` | integer | User account ID associated with the object. |
| `date_registered` | string | Customer registration date. Format: `Y-m-d H:i:s`. |
| `email_verification` | string | Email verification status. One of the following: `none` (email verification was not required), `pending`, `verified`. |
| `last_login` | string | Date the customer last logged in. Format: `Y-m-d H:i:s`. |
| `ips` | array | All known IP addresses for the customer. Recorded on login. |
| `notes` | string | Customer notes. |

## Create a customer

Create a new customer record.

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/wp-json/rcp/v1/customers/new</h6>
	</div>
</div>

```shell
curl -X POST https://example.com/wp-json/rcp/v1/customers/new \
	-H "Content-Type: application/json" \
	-d '{
  "user_id": 1,
  "date_registered": "2019-05-03 12:53:22",
  "email_verification": "none",
  "last_login": "2019-05-03 12:53:22"
}'
```

```javascript
$.ajax( {
    url: wpApiSettings.root + 'rcp/v1/customers/new',
    method: 'POST',
    beforeSend: function ( xhr ) {
        xhr.setRequestHeader( 'X-WP-Nonce', wpApiSettings.nonce );
    },
    data: {
    	user_id: 1,
		date_registered: '2019-05-03 12:53:22',
		email_verification: 'none',
		last_login: '2019-05-03 12:53:22'
    }
} ).done( function ( response ) {
    console.log( response );
} );
```

```php
<?php
$args = array(
	'body' => array(
		'user_id' => 1,
		'date_registered' => '2019-05-03 12:53:22',
		'email_verification' => 'none',
		'last_login' => '2019-05-03 12:53:22'
	)
);
$response = wp_remote_post( 'https://example.com/wp-json/rcp/v1/customers/new', $args );
?>
```

> Response: ID of the newly created customer

```json
1
```

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `user_id` | integer | ID of the associated user account. <i class="label label-info">required</i> |
| `date_registered` | string | Date the customer was registered. Format: `Y-m-d H:i:s`. Defaults to today if omitted. |
| `email_verification` | string | Email verification status: `verified`, `pending`, `none`.
| `last_login` | string | Date the customer last logged in. Format: `Y-m-d H:i:s`. |

## Retrieve a customer

## List all customers

## Update a customer

## Delete a customer
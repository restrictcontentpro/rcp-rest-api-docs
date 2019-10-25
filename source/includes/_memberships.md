# Memberships

Intro here.

## Membership object

The RCP_Membership class was released in version 3.0. It contains information and helper methods about a user's membership.

Do not create a new instance of the `RCP_Membership` class directly. Instead use `rcp_get_membership()` which returns an instance of this class.

### Retrieving membership data ###

All the properties in the `RCP_Membership` class are protected. To access this data, use our public helper methods:

```php
$membership = rcp_get_membership( 1 );
echo $membership->get_initial_amount( true );
```

> Response Example:

```
$14.99
```

| Method | Description |
| --------- | ----------- |
| `get_id()` | Returns the ID number of the membership. |
| `get_customer()` | Returns the `RCP_Customer` object associated with this membership. |
| `get_object_id()` | Returns the object ID number associated with this membership. This will be the ID of the membership level. |
| `get_object_type()` | Returns the type of object associated with this membership. At this time, RCP only has one object type so this will always return `membership`. |
| `get_currency()` | Returns the currency code used for this membership's payments, such as `USD`. |
| `get_initial_amount()` | Returns the amount charged on the initial signup. If `false` is passed in then just the integer or float value will be returned. If `true` is passed in then the result will be formatted with the currency symbol. Examples: |
| | `echo $membership->get_initial_amount( false );` |
| | This will print a plain number, like `14.99`. |
| | `echo $membership->get_initial_amount( true );` |
| | This will add the currency symbol in the correct place, like `$14.99`. |
| `get_recurring_amount()` | Returns the amount charged for renewal payments. If `false` is passed in then just the integer or float value will be returned. If `true` is passed in then the result will be formatted with the currency symbol. Examples: |
| | `echo $membership->get_recurring_amount( false );` |
| | This will print a plain number, like `14.99`. |
| | `echo $membership->get_recurring_amount( true );` |
| | This will add the currency symbol in the correct place, like `$14.99`. |

## Get a membership

```php
<?php $membership = rcp_get_membership( 1 ); ?>
```

> Response: RCP_Membership Object:

```json
{
  "id": 1,
  "activated_date": "2019-02-08 14:56:43",
  "auto_renew": 1,
  "cancellation_date": null,
  "created_date": "2019-02-08 14:56:43",
  "currency": "USD",
  "customer_id": 1,
  "date_modified": "2019-02-08 14:56:43",
  "disabled": 0,
  "expiration_date": "2020-02-08 23:59:59",
  "gateway": "stripe",
  "gateway_customer_id": "cus_123456789",
  "gateway_subscription_id": "sub_123456789",
  "initial_amount": 50,
  "maximum_renewals": 0,
  "notes": "",
  "object_id": 1,
  "object_type": "membership",
  "payment_plan_completed_date": null,
  "recurring_amount": 50,
  "renewed_date": null,
  "signup_method": "live",
  "status": "active",
  "subscription_key": "4d99db2ac8d75c0bb32f0f60ca69ae64",
  "times_billed": 1,
  "trial_end_date": null,
  "upgraded_from": 0,
  "uuid": "urn:uuid:a3673fd6-5fd2-4b4c-b315-ed7afae27678"
}
```

Retrieve a single membership record by ID.

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `$membership_id` | int | ID of the membership. |

## Query for memberships

```php
<?php
$memberships = rcp_get_memberships( array(
    'expiration_date_query' => array(
        'after' => '2020-01-01 00:00:00',
        'before' => '2020-01-31 23:59:59'
    ),
    'status' => 'active'
) );
?>
```

> Response: Array of RCP_Membership Objects:

```json
[
    {
      "id": 1,
      "activated_date": "2019-01-08 14:56:43",
      "auto_renew": 1,
      "cancellation_date": null,
      "created_date": "2019-01-08 14:56:43",
      "currency": "USD",
      "customer_id": 1,
      "date_modified": "2019-01-08 14:56:43",
      "disabled": 0,
      "expiration_date": "2020-01-08 23:59:59",
      "gateway": "stripe",
      "gateway_customer_id": "cus_123456789",
      "gateway_subscription_id": "sub_123456789",
      "initial_amount": 50,
      "maximum_renewals": 0,
      "notes": "",
      "object_id": 1,
      "object_type": "membership",
      "payment_plan_completed_date": null,
      "recurring_amount": 50,
      "renewed_date": null,
      "signup_method": "live",
      "status": "active",
      "subscription_key": "4d99db2ac8d75c0bb32f0f60ca69ae64",
      "times_billed": 1,
      "trial_end_date": null,
      "upgraded_from": 0,
      "uuid": "urn:uuid:a3673fd6-5fd2-4b4c-b315-ed7afae27678"
    }
]
```

Query for memberships.

| Parameter | Type | Description | Default |
| --------- | ---- | ----------- | ------- |
| `id` | int | A membership ID to only return that membership. | |
| `id__in` | array | An array of membership IDs to include. | |
| `id__not_in` | array | An array of membership IDs to exclude. | |

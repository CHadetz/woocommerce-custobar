# Woocommerce Custobar

This WordPress plugin is used to send usage statistics from the WooCommerce installation to the Custobar API.

Batch synchronization is run on plugin activation. This will upload all current Custobar compatible data to their API.

Afterwards synchronization is made only on updates of the related data. This is done by asynchronous API calls (utilizing scheduled events) after the relevant create or update action has been triggered. No data is removed or synced backwards from Custobar by this plugin nor does the API provide such functionality (as of this writing).

Relevant WooCommerce data has been mapped to the data fields offered by Custobar. Mapped data goes through WordPress filters so it's possible for site developers to add custom fields to the data before it gets sent to the Custobar API.

This plugin uses create and update hooks of WooCommerce's CRUD commands which were introduced in version 3.0, so no support for previous versions is provided.

Plugin code has been written following the PSR-2 coding standard.

For more information on Custobar API:
https://www.custobar.com/api/docs/

## Installation

@TODO

## Requires

- WooCommerce 3.x
- Tested with PHP 7.1 and WordPress 4.8

## Notices

- This plugin supports WooCommerce Subscriptions by adding custom fields for some basic information
- Order totals include VAT but order items do not (this is the default functionality of WooCommerce)
- Permission for marketing is asked in the checkout phase only for unauthenticated users. Usually customer do not register before the first order so practically this is rarely a problem. Permission is not given if it's not asked. This functionality might have to be changed if you offer a path to registration without purchase.
- Permission for marketing sets _email_ and _sms_ permissions if selected. No functionality to edit this through filters at this point.
- Custobar API often responds with _200 OK_ even when the data does not get uploaded, so do not trust the API response!

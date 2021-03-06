# PHP-Vanilla-Buycraft
A basic "BuyCraft" implementation written in PHP for pure vanilla Minecraft servers.

![demo](http://i.imgur.com/jJ8rJSz.gif)

# DISCLAIMER
This codebase has NOTHING to do with the official BuyCraft plugin or it's developers. I am simply borrowing the name to help users understand what this does, and what it's for. This is not a wrapper around BuyCraft or it's API. This is a stand-alone project with no real affiliation to BuyCraft

# Requirements
- A PayPal developer and business account (if using paypal)
- A PayPal developer app using the REST API (if using paypal)
- Composer
- php7.0.9+ (This is recommended, but not required. **I built this in php7.0.9, and cannot promise it will work in other versions!**)

# Commands and messages
In this current implementation, only one command is supported when an item is bought. This can easily be changed to be an array of commands which is looped, or by having the single command set a score/tag in-game, and then run more commands via command blocks on the server.

When a payment is successful, the script will run both the payment command as well as send a message in chat. This message is sent via `tellraw` targeting all players (`@a`) and uses JSON as it's input.

Both the command and message support several placeholders for data based on the purchase. See below for details

# Placeholders
> {product} -> placeholder which displays the bought product
> 
> {amount}  -> placeholder which displays the amount of the product
> 
> {price}   -> placeholder which displays the price of the product
> 
> {player}  -> placeholder which displays the player who bought the product

Example usage (command):
> give {player} stone {amount} 0

Example usage (message):
> {"text":"Thank you {player} for the donation of {price}, enjoy your {product}!"}

# Ports
- __[PHP (Slim3+Twig) - Uses PayPal](https://github.com/RedDuckss/PHP-Vanilla-Buycraft/)__

# Setup
## For an explanation on the core concepts used here, refer to *Soon-to-be-video-url*
To build from source:
- Clone the repo and open the root directory
- Change any class and path namespaces as you see fit (defaults to `VBCraft`)
- Install all dependencies via `composer install` (requires Composer)
- Travel to the `app` folder
- Edit `app.php` to match your PayPal app keys and database credentials
- Travel to the `public` folder
- Edit `install.php` to match your database credentials
- Run `install.php`
### To host this project as-is you must have either a shared host which gives you access to composer/SSH or a VPS and install composer in order to download the dependencies. I recommend XenonHosting, as they have very affordable shared hosting (starting at $1/m) with SSH access, and VPS hosting starting at $3/m [http://xenonhosting.co.uk/](http://xenonhosting.co.uk/)

# Going Live
When working with the PayPal REST api you are given 2 sets of client/secret keys. One key is for sandbox use and one is for live use. Sandbox use does NOT use real money, and does NOT accept real PayPal accounts for transactions (only test sandbox accounts, which you create). **YOU SHOULD ONLY DEVELOP WHILE IN SANDBOX MODE, USING THE SANDBOX KEYS**. To go live and accepting REAL payments from REAL customers, you must change the client/secret keys to the `Live` keys, as well as uncomment the `Going Live` section of `app.php`

# Adding sections and items
This repo is **NOT** meant to be used as-is, though there is basic as-is support. This repo is designed to be a base with which you build your **OWN** application(s). That being said, if you MUST use this repo as-is, you can add sections and items very easily.
- Open the `vanillabuycraft` database in any database editor
- Edit `shopsections` to add new sections
- Edit `shopitems` to add new items to those sections

# Can I contribute?
Yes you can! If you would like to contribute to this codebase, feel free to hack away at it and make a Pull Request. If you have ported this code to another language/payment service provider, make an Issue post or a Pull Request with a change to this README linking to the port and I will add a link here.

# Libraries Used
* __[PHP Minecraft Rcon](https://github.com/thedudeguy/PHP-Minecraft-Rcon)__
* __[PayPal PHP SDK](https://github.com/paypal/PayPal-PHP-SDK)__

# Licensing information

	This program is free software: you can redistribute it and/or modify
	it under the terms of the GNU Affero General Public License as published by
	the Free Software Foundation, either version 3 of the License, or
	(at your option) any later version.

	This program is distributed in the hope that it will be useful,
	but WITHOUT ANY WARRANTY; without even the implied warranty of
	MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
	GNU Affero General Public License for more details.

	You should have received a copy of the GNU Affero General Public License
	along with this software. If not, see <http://www.gnu.org/licenses/>.

Vanilla BuyCraft is not, nor am I (Jonathan Barrow), affiliated with Mojang or the official BuyCraft service. All brands and trademarks belong to their respective owners. Vanilla BuyCraft is not a Mojang-approved software, nor is it associated with Mojang.

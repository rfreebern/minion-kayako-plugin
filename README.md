Kayako
======

A plugin for [Minion](http://github.com/rfreebern/minion). With access to a
[Kayako](http://kayako.com) support system MySQL database, can retrieve and
summarize information about specific tickets.

Depends on the (built in) DB plugin, connected to a MySQL or SQLite database.

**Note:** Currently, the Kayako database must reside on the same MySQL host
that the DB plugin uses for other data. Only tested against Kayako
SupportSuite 3.70.02.

Installation
------------

Place `Kayako.php` in `plugins/Kayako/` in your Minion install. If your Minion
install is a git repository, you can

    git submodule add https://github.com/rfreebern/minion-kayako-plugin.git plugins/Kayako

from the Minion base directory.

Configuration
-------------

Requires two configuration parameters in `config.php`:

* KayakoDB

  The name of the MySQL database where your Kayako ticket information is stored.

* URL

  The URL prefix your staff uses to view tickets.

Example:

    $this->PluginConfig['Kayako'] = array(
        'KayakoDB' => 'your_kayako_db_name',
        'URL' => 'http://support.yoursite.com/staff'
    );

Usage
-----

* `!ticket last`

  Displays ticket information for the last ticket filed.

* `!ticket ABC-123456`

  Diplsays ticket information for the ticket with public-facing ID `ABC-123456`.

* `!ticket 98765`

  Displays ticket information for the ticket with internal ID `98765`.

Example ticket information display:

    <Azazel> Ticket ABC-123456: Error on site [Julie Smith / jsmith@exampleclient.com] [Created 2013-02-09 08:55:17] [Updated 2013-02-09 09:12:41] [1 replies] http://support.yoursite.com/staff/?_m=tickets&_a=viewticket&ticketid=98765

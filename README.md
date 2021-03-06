# Fluent::Plugin::Snmp, a plugin for [Fluentd](http://fluentd.org)

Fluentd snmp input plugin

## Installation

Add this line to your application's Gemfile:

    gem 'fluent-plugin-snmp'

Or install it yourself as:

    $ gem install fluent-plugin-snmp

## Usage

    <source>
      type snmp
      tag snmp.server1
      nodes name, value
      host localhost
      community public
      mib sysContact.0, sysDescr.0, sysName.0
      method_type get
      polling_time 5
      polling_type async_run
    </source>
    
    <source>
      type snmp
      tag snmp.server2
      host localhost
      community public
      mib hrStorageIndex, hrStorageDescr, hrStorageSize, hrStorageUsed
      mib_modules HOST-RESOURCES-MIB
      polling_time 0,10,20,30,40,50
      out_executor sample/out_exec.rb.sample
    </source>
    
    <match snmp.server*>
      type stdout
    </match>

## Copyright
Copyright (c) 2012 Internet Initiative Inc.
Apache Licence, Version 2.0

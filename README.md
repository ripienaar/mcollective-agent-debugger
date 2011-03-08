What?
=====

An interactive debugger for MCollective Agents

How?
====

<pre>
% mc-debugger
type "help" for help using this debugger
>> result = call :filemgr, :status, :file => "/tmp"
debug 2011/03/08 17:47:18: pluginmanager.rb:83:in `loadclass' Loading MCollective::Agent::Filemgr from mcollective/agent/filemgr.rb
debug 2011/03/08 17:47:18: pluginmanager.rb:36:in `&lt;&lt;' Registering plugin filemgr_agent with class MCollective::Agent::Filemgr
debug 2011/03/08 17:47:18: ddl.rb:56:in `findddlfile' Found filemgr ddl at /usr/libexec/mcollective/mcollective/agent/filemgr.ddl
debug 2011/03/08 17:47:18: pluginmanager.rb:73:in `[]' Returning plugin filemgr_agent with class MCollective::Agent::Filemgr
debug 2011/03/08 17:47:18: pluginmanager.rb:73:in `[]' Returning plugin connector_plugin with class NoopConnector
debug 2011/03/08 17:47:18: filemgr.rb:63:in `status' Asked for status of '/tmp' - it is present
debug 2011/03/08 17:47:18: ddl.rb:56:in `findddlfile' Found filemgr ddl at /usr/libexec/mcollective/mcollective/agent/filemgr.ddl

local_invocation
         Change time:
        Tue Mar 08 17:43:14 +0000 2011
                Type: directory
               Owner: 0
             Present: 1
               Group: 0
   Modification time: 1299606194
              Status: present
         Change time: 1299606194
         Access time:
        Tue Mar 08 16:48:54 +0000 2011
                Size: 4096
         Access time: 1299602934
                Name: /tmp
   Modification time:
        Tue Mar 08 17:43:14 +0000 2011
                Mode: 41777
                 MD5: 0

=> {:data=>{:ctime=>Tue Mar 08 17:43:14 0000 2011, :type=>"directory", :uid=>0, :present=>1, :gid=>0, :mtime_seconds=>1299606194, :output=>"present", :ctime_seconds=>1299606194, :atime=>Tue Mar 08 16:48:54 0000 2011, :size=>4096, :atime_seconds=>1299602934, :name=>"/tmp", :mtime=>Tue Mar 08 17:43:14 0000 2011, :mode=>"41777", :md5=>0}, :statuscode=>0, :statusmsg=>"OK"}
>> pp result
{:data=>
  {:ctime=>Tue Mar 08 17:43:14 +0000 2011,
   :type=>"directory",
   :uid=>0,
   :present=>1,
   :gid=>0,
   :mtime_seconds=>1299606194,
   :output=>"present",
   :ctime_seconds=>1299606194,
   :atime=>Tue Mar 08 16:48:54 +0000 2011,
   :size=>4096,
   :atime_seconds=>1299602934,
   :name=>"/tmp",
   :mtime=>Tue Mar 08 17:43:14 +0000 2011,
   :mode=>"41777",
   :md5=>0},
 :statuscode=>0,
 :statusmsg=>"OK"}
=> nil
</pre>

This lets you call an agent interactively as if the mcollectived was calling it.  Each invocation of _call_ will freshly load the agent from disk so you can just edit, save and call no need to restart the debugger.

It will use the same code that _printrpc_ does to show your result using the DDL so can also be used to debug DDL issues

The return will be the full SimpleRPC style result and logging will always be in debug mode.

It will use your normal mcollective config file to find the libdir, you can specify an alternative config file as the first argument on the command line

Contact?
========

R.I.Pienaar <rip@devco.net> / www.devco.net / @ripienaar

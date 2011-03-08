What?
=====

An interactive debugger for MCollective Agents

How?
====

<pre>
% mc-debugger
type "help" for help using this debugger
>> r = call("filemgr", "status", :file => "/tmp")
debug 2011/03/08 17:03:58: pluginmanager.rb:83:in `loadclass' Loading MCollective::Agent::Filemgr from mcollective/agent/filemgr.rb
debug 2011/03/08 17:03:58: pluginmanager.rb:36:in `&lt;&lt;' Registering plugin filemgr_agent with class MCollective::Agent::Filemgr
debug 2011/03/08 17:03:58: ddl.rb:56:in `findddlfile' Found filemgr ddl at /usr/libexec/mcollective/mcollective/agent/filemgr.ddl
debug 2011/03/08 17:03:58: pluginmanager.rb:73:in `[]' Returning plugin filemgr_agent with class MCollective::Agent::Filemgr
debug 2011/03/08 17:03:58: pluginmanager.rb:73:in `[]' Returning plugin connector_plugin with class NoopConnector
debug 2011/03/08 17:03:58: filemgr.rb:63:in `status' Asked for status of '/tmp' - it is present
=> {:statuscode=>0, :data=>{:ctime=>Tue Mar 08 17:02:37 0000 2011, :type=>"directory", :ctime_seconds=>1299603757, :output=>"present", :uid=>0, :atime_seconds=>1299602934, :gid=>0, :md5=>0, :atime=>Tue Mar 08 16:48:54 0000 2011, :size=>4096, :present=>1, :name=>"/tmp", :mtime=>Tue Mar 08 17:02:37 0000 2011, :mode=>"41777", :mtime_seconds=>1299603757}, :statusmsg=>"OK"}
>> pp r
{:statuscode=>0,
 :data=>
  {:ctime=>Tue Mar 08 17:02:37 +0000 2011,
   :type=>"directory",
   :ctime_seconds=>1299603757,
   :output=>"present",
   :uid=>0,
   :atime_seconds=>1299602934,
   :gid=>0,
   :md5=>0,
   :atime=>Tue Mar 08 16:48:54 +0000 2011,
   :size=>4096,
   :present=>1,
   :name=>"/tmp",
   :mtime=>Tue Mar 08 17:02:37 +0000 2011,
   :mode=>"41777",
   :mtime_seconds=>1299603757},
 :statusmsg=>"OK"}
=> nil
</pre>

This lets you call an agent interactively as if the mcollectived was calling it.  Each invocation of _call_ will freshly load the agent from disk so you can just edit, save and call no need to restart the debugger.

The return will be the full SimpleRPC style result and logging will always be in debug mode.

It will use your normal mcollective config file to find the libdir, you can specify an alternative config file as the first argument on the command line

Contact?
========

R.I.Pienaar <rip@devco.net> / www.devco.net / @ripienaar

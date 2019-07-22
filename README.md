# test-puppet
Create/extend an existing puppet module for Nginx including the following functionalities:

    Create a proxy to redirect requests for https://domain.com to 10.10.10.10 and redirect requests for https://domain.com/resource2 to 20.20.20.20.
    Create a forward proxy to log HTTP requests going from the internal network to the Internet including: request protocol, remote IP and time take to serve the request.
    
I use the Nginx module for Puppet found here: https://github.com/voxpupuli/puppet-nginx

Install it with `puppet module install puppet-nginx`
If you need to find your modulepath: `puppet config print modulepath`.

Then you can execute the manifests locally (on your computer, a virtual machine... it's up to you) with
the necessary permissions (use sudo if necessary or as root if you require) with
`puppet apply --modulepath=path-to-your-modulepath path-to-manifest.pp`

The first instruction is executed by 1-reverse_proxy.pp and the second instruction is executed
by 2-forward_proxy-logging.pp.

In order to test the forward proxy you can point a web browser to use the proxy called `localhost` (on the local host!)
on port 8080. You will find the logs in the default location (it could be something like `/var/log/nginx/localhost.access.log`
with the required information.

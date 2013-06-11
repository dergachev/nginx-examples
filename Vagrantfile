# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"

  config.vm.provision :shell, :inline => <<-EOT
    apt-get update
    apt-get -y install vim curl git nginx
  EOT

  # install conditional-blocking and run tests
  config.vm.provision :shell, :inline => <<-EOT
    ln -s /vagrant/nginx-conf/conditional-blocking /etc/nginx/sites-enabled/conditional-blocking
    service nginx restart

    #TODO: finish this function and use it!
    assertCurlStatus()
    {
      export CURL_CMD="curl $1 -o /dev/null -s -i -w '%{http_code}'"
      echo "$CURL_CMD | grep $2"
    }
    # assertCurlStatus '-A "Suspicious" localhost:8000/bb' 405

    # suspicious IP, suspicious user agent
    curl -A "Suspicious" localhost:8000/index.html -o /dev/null -s -i -w '%{http_code}' | grep 403 || exit 3
    # suspicious IP, not suspicious user agent, HEAD request
    curl -I -A "Not Suspicious" localhost:8000/index.html -o /dev/null -s -i -w '%{http_code}' | grep 403 || exit 3
    # suspicious IP, not suspicious user agent, not HEAD
    curl -A "Not Suspicious" localhost:8000/index.html -o /dev/null -s -i -w '%{http_code}' | grep 200 || exit 3
    # ok IP, suspicious user agent
    curl -A "Suspicious" 10.0.2.15:8000/index.html -o /dev/null -s -i -w '%{http_code}' | grep 200 || exit 3
    # ok IP, ok user agent, HEAD
    curl -I -A "Not Suspicious" 10.0.2.15:8000/index.html -o /dev/null -s -i -w '%{http_code}' | grep 200 || exit 3
  EOT
end

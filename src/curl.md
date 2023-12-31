# Good to know cURL options

* Download to file using filename from URL: `-O` | `--remote-name`

* Silent: `-s` | `--silent`. Don't show the progress bar.

* Follow redirects: `-L` | `--location`

* Retries: `--retry <n>`

* Fail silently on HTTP errors / bad status codes: `-f` | `--fail`

* Include response headers in output: `-i` | `--include`

* Username/password: `-u username:pass`

* Client certs: `--cert cert-w-key.pem:password` or `--cert cert.crt --key key.key`

* Allow insecure TLS connections (i.e. untrusted certs): `-k` | `--insecure`

* STDIN as body: `-d@-`.
  E.g. `cat f.json | curl -H "Content-Type: application/json" -d @- http://api`

* json (curl >= 7.82):
  `jo name=christian tool=curl | curl --json @- http://api | jq`

* Override dns resolve: `curl https://domain.example --connect-to domain.example:443:203.0.113.81:443`

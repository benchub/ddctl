# ddctl - Datadog Downtime Controller
#### Requirements
* `pip install datadog`
* API and APP key from Datadog

#### Setup config for Datadog API
* Create a Datadog API config file and structure it like this:
~~~~
[ddctl]
api_key = 9775a026f1ca7d1c6c5af9d94d9595a4
app_key = 87ce4a24b5553d2e482ea8a8500e71b8ad4554ff
~~~~
*This is a dummy API and APP key used in Datadog API documentation*

* ddctl defaults to ddctl.conf in executables directory
  * Use the `--config` flag to point to a custom config location.

#### Example usage
* Query for all hosts matching a 'string':
  * `ddctl --query string`
* Query for all hosts matching a 'string' and return in csv:
  * `ddctl --query string --csv`
* Mute a host using defaults (Defaults to 2 hours downtime):
  * `ddctl --mute --host <hostname>`
  * `ddctl --mute --host <hostname> --force` to FORCE default values
* Mute a host and request no end time (forever):
  * `ddctl --mute --host <hostname> --forever`
  * `ddctl --mute --host <hostname> --forever --force` to FORCE no end time
* Mute a host and request a specific end time in hours from now:
  * `ddctl --mute --host <hostname> --hours <#_hours>`
  * `ddctl --mute --host <hostname> --hours <#_hours> --force` to FORCE specified hours
* Unmute a host:
  * `ddctl --unmute --host <hostname>`
* Example usage of mute/unmute hosts with csv output:
  * `./ddctl --unmute --host $(./ddctl --query string --csv)`
  * `./ddctl --mute --host $(./ddctl --query string --csv)`
  * `./ddctl --mute --host $(./ddctl --query string --csv) --forever`
  * `./ddctl --mute --host $(./ddctl --query string --csv) --hours <#_hours>`

# wireshark-thrift-dissector

A wireshark dissector for thrift messages.

Currently this package contains a generic dissector that can decode thrift messages. Thrift messages only contain field
ids, not names, so you will have to refer to the Thrift IDL to determine what a given field maps to.

## Protocols Supported

* THeader protocol with a TBinary message

## Configuration
Currently, you can edit the `default-settings` table in `thrift-generic.lua`

* `default_port`: Sets the default port for the dissector. (default: 9090)

## Usage

`wireshark -X lua_script:thrift-generic.lua path/to/your/capture.pcap`

By default, port 9090 will be dissected. You can add additional ports with `Decode as...`, or change `default_port` in
the configuration.

## Known Issues / TODOs
* Performance is a bit slow with large fragmented messages. This can probably be improved through parsing partial
messages, currently the dissector buffers fragmented messages until the full message can be dissected.
* Only supports the THeader protocol currently, can be extended to support non-headered TFramed messages.
* Add configuration via preferences

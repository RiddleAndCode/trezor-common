
all: combine

check: combined.pb combined.pb

%.pb: %.proto
	protoc -I/usr/include -I. $< -o $@

combine:
	echo 'syntax = "proto2";' > combined.proto
	echo 'import "google/protobuf/descriptor.proto";' >> combined.proto
	grep -hv -e '^import ' -e '^syntax' -e '^package' -e 'option java_' messages*.proto | sed 's/hw\.trezor\.messages\.common\.//' >> combined.proto
	$(MAKE) combined.pb

clean:
	rm -f *.pb

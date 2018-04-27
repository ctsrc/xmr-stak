# xmr-stak – Fedora 27 / AMD Ryzen 7 1700

Personalized README for CPU mining with [fireice-uk/xmr-stak](https://github.com/fireice-uk/xmr-stak) on my workstation.

This README is current as of commit [26a5d65](https://github.com/ctsrc/xmr-stak/commit/26a5d65f12b2f19a0a3ece39a2bc64718796367b) to the xmr-stak master branch.

## Usage

```sh
cd ~/src/github.com/fireice-uk/xmr-stak/build/
./bin/xmr-stak --currency monero7 \
  -o stratum+tcp://cryptonightv7.eu.nicehash.com:3363 \
  -u 3Qsz9ZbmxYojJcGxwm2KqG631yA38wt7gY.CPU -p x -r '' \
  --use-nicehash -i 8037
```

## Build from source

```bash
sudo dnf install libmicrohttpd-devel openssl-devel cmake hwloc-devel
mkdir -p ~/src/github.com/fireice-uk
cd !$
git clone https://github.com/fireice-uk/xmr-stak.git
mkdir xmr-stak/build
cd xmr-stak/build
cmake -DCUDA_ENABLE=OFF -DOpenCL_ENABLE=OFF ..
make install
```

## Enable large page support and increase ulimit -l

See https://github.com/xmrig/xmrig/issues/32 and
https://github.com/fireice-uk/xmr-stak/blob/master/doc/FAQ.md#error-memory-alloc-failed-mmap-failed

```bash
echo vm.nr_hugepages=128 | sudo dd oflag=append conv=notrunc of=/etc/sysctl.conf
sudo sysctl -p

sudo dd oflag=append conv=notrunc of=/etc/security/limits.conf <<EOF
* soft memlock 262144
* hard memlock 262144
EOF
```

Log out and then log back in for the ulimit take effect.

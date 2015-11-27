# statsderl

__Author:__ Louis-Philippe Gauthier.

Non-blocking Erlang Memcached client

[![Build Status](https://travis-ci.org/lpgauth/statsderl.svg?branch=dev)](https://travis-ci.org/lpgauth/statsderl)

### Requirements

* Erlang 16.0 +

## Tests

```makefile
make test
```

### Environment variables

<table width="100%">
  <theader>
    <th>Name</th>
    <th>Type</th>
    <th>Default</th>
    <th>Description</th>
  </theader>
  <tr>
    <td>base_key</td>
    <td>hostname | name | sname | undefined | io:data()</td>
    <td>undefined</td>
    <td>key prefrix</td>
  </tr>
  <tr>
    <td>hostname</td>
    <td>inet:ip_address() | binary() | list()</td>
    <td>{127, 0, 0, 1}</td>
    <td>server hostname</td>
  </tr>
  <tr>
    <td>port</td>
    <td>pos_integer()</td>
    <td>8125</td>
    <td>server port</td>
  </tr>


</table>

## API
<a href="http://github.com/lpgauth/statsderl/blob/master/dev/statsderl.md#index" class="module">Function Index</a>

## Examples

```erlang
1> statsderl:counter(["test", $., "counter", 1, 0.23).
ok.

2> statsderl:decrement("test.decrement", 1, 0.5).
ok.

3> statsderl:gauge([<<"test">>, $., "gauge"], 333, 1.0).
ok.

4> statsderl:gauge_decrement([<<"test.gauge_decrement"], 15, 0.001).
ok.

5> statsderl:gauge_increment(<<"test.gauge_increment">>, 32, 1).
ok.

6> statsderl:increment(<<"test.increment">>, 1, 1).
ok.

7> statsderl:timing("test.timing", 5, 0.5).
ok

8> statsderl:timing_fun(<<"test.timing">>, fun() -> timer:sleep(100) end, 0.5).

9> Timestamp = os:timestamp(),
{1448,591778,258983}

10> statsderl:timing_now("test.timing", Timestamp, 0.15).
```

## License

```license
Copyright (c) 2011-2015, Louis-Philippe Gauthier
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:
    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in the
      documentation and/or other materials provided with the distribution.
    * Neither the name of the BLOOM Digital Platforms nor the
      names of its contributors may be used to endorse or promote products
      derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL BLOOM DIGITAL PLATFORMS BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

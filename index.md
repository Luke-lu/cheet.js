```javascript
cheet('i d d q d', function () {
  alert('god mode enabled');
});
```

```javascript
cheet('up up down down left right left right b a', {
  next: function (str, key, num, seq) {
    console.log('key pressed: ' + key);
    console.log('progress: ' + num / seq.length);
    console.log('seq: ' + seq.join(' '));
  },

  fail: function () {
    console.log('sequence failed');
  },

  done: function () {
    console.log('+30 lives ;)');
  }
});
```

```javascript
cheet('o n c e', function () {
  console.log('This will only fire once.');
  cheet.disable('o n c e');
});
```

```javascript
var sequences = {
  cross: 'up down left right',
  circle: 'left up right down'
};

cheet(sequences.cross);
cheet(sequences.circle);

cheet.done(function (seq) {
  if (seq === sequences.cross) {
    console.log('cross!');
  } else {
    console.log('circle!');
  }
});
```

### Demo

[My personal site](http://namuol.github.io) uses cheet.js (Try the [Konami Code](http://en.wikipedia.org/wiki/Konami_Code))

### Install

#### bower

    bower install cheet.js

&nbsp;

    <script src="/bower_components/cheet.js/cheet.min.js" type="text/javascript"></script>

### API

<a name='api_cheet'></a>
#### [`cheet(sequence, done | {next,fail,done})`](#api_cheet)

Map a sequence of keypresses to a callback. This can be called multiple times.

> <a name='api_cheet_sequence'></a>
> [`sequence`](#api_cheet_sequence) (String)
> > A string representation of a sequence of [key names](#available-key-names).
> > 
> > Each keyname must be separated by a single space.
> 
> <a name='api_cheet_done'></a>
> [`done(str, seq)`](#api_cheet_done) (callback)
> > A callback to execute each time the sequence is correctly pressed.
> > 
> > Arguments:
> > * `str` - The string representation of the sequence that completed.
> > * `seq` - An array of [key names](#available-key-names) representing the sequence that completed.
> 
> <a name='api_cheet_fail'></a>
> [`fail(str, seq)`](#api_cheet_fail) (callback)
> > A callback to execute each time a sequence's progress is broken.
> > 
> > Arguments:
> > * `str` - The string representation of the sequence that failed.
> > * `seq` - An array of [key names](#available-key-names) representing the sequence that was pressed.
>
> <a name='api_cheet_next'></a>
> [`next(str, key, num, seq)`](#api_cheet_next) (callback)
> > A callback to execute each time a correct key in the sequence is pressed *in order*.
> > 
> > Arguments:
> > * `str` - The string representation of the sequence that is in progress.
> > * `key` - The [name of the key](#available-key-names) that was just pressed.
> > * `num` - A number representing the current progress of the sequence. (starts at 0)
> > * `seq` - An array of [key names](#available-key-names) representing the sequence that is in progress.

<a name='api_done'></a>
#### [`cheet.done(callback)`](#api_done)

Set a global callback that executes whenever *any* mapped sequence is completed successfully.

> <a name='api_done_callback'></a>
> [`done(str, seq)`](#api_done_callback) (callback)
> > A callback to execute each time *any* sequence is correctly pressed.
> > 
> > Arguments:
> > * `str` - The string representation of the sequence that completed.
> > * `seq` - An array of [key names](#available-key-names) representing the sequence that completed.

<a name='api_next'></a>
#### [`cheet.next(callback)`](#api_next)

Set a global callback that executes whenever *any* mapped sequence progresses.

> <a name='api_next_callback'></a>
> [`callback(str, key, num, seq)`](#api_next_callback) (callback)
> > A callback to execute each time a correct key in any sequence is pressed *in order*.
> > 
> > Arguments:
> > * `str` - The string representation of the sequence that is in progress.
> > * `key` - The [name of the key](#available-key-names) that was just pressed.
> > * `num` - A number representing the current progress of the sequence. (starts at 0)
> > * `seq` - An array of [key names](#available-key-names) representing the sequence that is in progress.

<a name='api_fail'></a>
#### [`cheet.fail(callback)`](#api_fail)

Set a global callback that executes whenever *any* in-progress sequence is broken.

> <a name='api_fail_callback'></a>
> [`callback(str, seq)`](#api_fail_callback) (callback)
> > A callback to execute each time *any* sequence's progress is broken.
> > 
> > Arguments:
> > * `str` - The string representation of the sequence that failed.
> > * `seq` - An array of [key names](#available-key-names) representing the sequence that was pressed.

<a name='api_disable'></a>
#### [`cheet.disable(sequence)`](#api_disable)

Disable a previously-mapped sequence.

> <a name='api_disable_sequence'></a>
> [`sequence`](#api_disable_sequence) (String)
> > The same string you used to map the callback when using [`cheet(seq, ...)`](#api_cheet).

### Available Key Names

**NOTE**: Key names are case-sensitive

#### Directionals
* `left`
* `L` (alias for `left`)
* `up`
* `U` (alias for `up`)
* `right`
* `R` (alias for `right`)
* `down`
* `D` (alias for `down`)

#### Alphanumeric
* `0`-`9` (main number keys)
* `a`-`z`

#### Misc 
* `backspace`
* `tab`
* `enter`
* `return` (alias for `enter`)
* `shift`
* `ctrl`
* `alt`
* `pause`
* `capslock`
* `esc`
* `space`
* `pageup`
* `pagedown`
* `end`
* `home`
* `insert`
* `delete`
* `equal`
* `=` (alias for `equal`)
* `comma`
* `,` (alias for `comma`)
* `minus`
* `-` (alias for `minus`)
* `period`
* `.` (alias for `period`)

#### Keypad
* `kp_0`-`kp_9`
* `kp_multiply`
* `kp_plus`
* `kp_minus`
* `kp_decimal`
* `kp_divide`

#### Function keys
* `f1`-`f12`

### TODO

Automated tests and travis-ci integration.

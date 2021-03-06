<a name="module_chord"></a>

# chord
[![npm version](https://img.shields.io/npm/v/tonal-chord.svg)](https://www.npmjs.com/package/tonal-chord)
[![tonal](https://img.shields.io/badge/tonal-chord-yellow.svg)](https://www.npmjs.com/browse/keyword/tonal)

`tonal-chord` is a collection of functions to manipulate musical chords

This is part of [tonal](https://www.npmjs.com/package/tonal) music theory library.

**Example**  
```js
const chord = require('tonal-chord')
chord.notes('CMaj7') // => ['C', 'E', 'G', 'B']
```

* [chord](#module_chord)
    * [`.names(aliases)`](#module_chord.names) ⇒ <code>Array</code>
    * [`.props(name)`](#module_chord.props) ⇒ <code>Object</code>
    * [`.intervals(name)`](#module_chord.intervals) ⇒ <code>Array.&lt;String&gt;</code>
    * [`.notes(nameOrTonic)`](#module_chord.notes) ⇒
    * [`.exists(name)`](#module_chord.exists) ⇒ <code>Boolean</code>
    * [`.tokenize(name)`](#module_chord.tokenize) ⇒ <code>Array</code>
    * [`~position(chord)`](#module_chord..position) ⇒ <code>Integer</code>

<a name="module_chord.names"></a>

## `chord.names(aliases)` ⇒ <code>Array</code>
Return the available chord names

**Kind**: static method of [<code>chord</code>](#module_chord)  
**Returns**: <code>Array</code> - the chord names  

| Param | Type | Description |
| --- | --- | --- |
| aliases | <code>boolean</code> | true to include aliases |

**Example**  
```js
import * as chord from 'tonal-chord'
chord.names() // => ['maj7', ...]
```
<a name="module_chord.props"></a>

## `chord.props(name)` ⇒ <code>Object</code>
Get chord properties. It returns an object with :
- name: the chord name
- names: a list with all possible names (includes the current)
- intervals: an array with the chord intervals
- chroma:  chord croma (see pcset)
- setnum: chord chroma number

**Kind**: static method of [<code>chord</code>](#module_chord)  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>String</code> | the chord name (without tonic) |

<a name="module_chord.intervals"></a>

## `chord.intervals(name)` ⇒ <code>Array.&lt;String&gt;</code>
Get chord intervals. It always returns an array

**Kind**: static method of [<code>chord</code>](#module_chord)  
**Returns**: <code>Array.&lt;String&gt;</code> - a list of intervals or null if the type is not known  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>String</code> | the chord name (optionally a tonic and type) |

<a name="module_chord.notes"></a>

## `chord.notes(nameOrTonic)` ⇒
Get the chord notes of a chord. This function accepts either a chord name
(for example: 'Cmaj7') or a list of notes.

It always returns an array, even if the chord is not found.

**Kind**: static method of [<code>chord</code>](#module_chord)  
**Returns**: [String] name - (Optional) name if the first parameter is the tonic  

| Param | Type | Description |
| --- | --- | --- |
| nameOrTonic | <code>String</code> | name of the chord or the tonic |

**Example**  
```js
chord.notes('Cmaj7') // => ['C', 'E', 'G', 'B']
chord.notes('C', 'maj7') // => ['C', 'E', 'G', 'B']
```
<a name="module_chord.exists"></a>

## `chord.exists(name)` ⇒ <code>Boolean</code>
Check if a given name correspond to a chord in the dictionary

**Kind**: static method of [<code>chord</code>](#module_chord)  

| Param | Type |
| --- | --- |
| name | <code>String</code> | 

**Example**  
```js
chord.exists('CMaj7') // => true
chord.exists('Maj7') // => true
chord.exists('Ablah') // => false
```
<a name="module_chord.tokenize"></a>

## `chord.tokenize(name)` ⇒ <code>Array</code>
Tokenize a chord name. It returns an array with the tonic and chord type 
If not tonic is found, all the name is considered the chord name.

This function does NOT check if the chord type exists or not. It only tries
to split the tonic and chord type.

**Kind**: static method of [<code>chord</code>](#module_chord)  
**Returns**: <code>Array</code> - an array with [type, tonic]  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>String</code> | the chord name |

**Example**  
```js
chord.tokenize('Cmaj7') // => [ 'C', 'maj7' ]
chord.tokenize('C7') // => [ 'C', '7' ]
chord.tokenize('mMaj7') // => [ null, 'mMaj7' ]
chord.tokenize('Cnonsense') // => [ 'C', 'nonsense' ]
```
<a name="module_chord..position"></a>

## `chord~position(chord)` ⇒ <code>Integer</code>
Get the position (inversion number) of a chord (0 is root position, 1 is first
inversion...). It assumes the chord is formed by superposed thirds.

**Kind**: inner method of [<code>chord</code>](#module_chord)  
**Returns**: <code>Integer</code> - the inversion number (0 for root inversion, 1 for first
inversion...) or null if not a valid chord  

| Param | Type | Description |
| --- | --- | --- |
| chord | <code>Array</code> \| <code>String</code> | the chord notes |

**Example**  
```js
chord.position('e g c') // => 1
chord.position('g3 e2 c5') // => 1 (e is the lowest note)
```

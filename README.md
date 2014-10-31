SherlockJS
=========

####Sherlock parses events written in plain English, and returns an object defining a basic event.

It was designed to allow event creation using natural language. For example, "The party is tomorrow from 3pm to 5pm." will return:

```javascript
{
  eventTitle: 'The party',
  startDate: Sat Dec 01 2012 15:00:00 GMT-0600 (CST),
  endDate: Sat Dec 01 2012 17:00:00 GMT-0600 (CST),
  isAllDay: false
}
```

## Setup

Installation is very typical.

```bash
$ npm install sherlockjs --save
```

## Usage

```javascript
var Sherlock = require('sherlockjs');
var sherlocked = Sherlock.parse('Homework 5 due next monday at 3pm');

// Basic properties
var title = sherlocked.eventTitle;    // 'Homework 5 due'
var startDate = sherlocked.startDate; // Date object pointing to next monday at 3pm
var endDate = sherlocked.endDate;     // null in this case, since no duration was given
var isAllDay = sherlocked.isAllDay;   // false, since a time is included with the event

// Example of an additional custom property added by Watson
var validated = sherlocked.validated; // true
```

## Methods
There are 2 methods in Sherlock.js.

**Sherlock.parse(String)**

`Sherlock.parse()` takes a string representing some English phrase, and returns an object with the following properties:

* `eventTitle` - string representing Sherlock's best guess at what the event title should be, or `null` if no title found.
* `startDate` - Date object representing start of the event, or `null` if not found.
* `endDate` - Date object representing end of the event, or `null` if not found.
* `isAllDay` - `true` if the input string describes an all-day event, otherwise `false`.

**Sherlock._setNow(Date)**

`Sherlock._setNow()` allows you to change what time Sherlock thinks it is right now, regardless of the system clock.

Pass in a Date object, and Sherlock will parse strings as if they there were entered on that day and time.
Pass in `null` to clear your custom date and use the system time instead.

This method is primarily meant for debugging purposes.

## License

The MIT License (MIT)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

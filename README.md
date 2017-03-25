# api-documentation for  [agenda (v0.9.1)](https://github.com/rschmukler/agenda#readme)  [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-agenda.svg)](https://travis-ci.org/npmdoc/node-npmdoc-agenda)
#### Light weight job scheduler for Node.js

[![NPM](https://nodei.co/npm/agenda.png?downloads=true)](https://www.npmjs.com/package/agenda)

# html version

- [https://npmdoc.github.io/node-npmdoc-agenda/build..beta..travis-ci.org/apidoc.html](https://npmdoc.github.io/node-npmdoc-agenda/build..beta..travis-ci.org/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-agenda/build/screen-capture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-agenda_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-agenda/build..beta..travis-ci.org/apidoc.html)

# package-listing

![package-listing](https://npmdoc.github.io/node-npmdoc-agenda/build/screen-capture.npmPackageListing.svg)



# package.json

```json

{
    "author": {
        "name": "Ryan Schmukler",
        "email": "ryan@slingingcode.com",
        "url": "http://slingingcode.com/"
    },
    "bugs": {
        "url": "https://github.com/rschmukler/agenda/issues"
    },
    "dependencies": {
        "cron": "~1.1.0",
        "date.js": "~0.3.1",
        "human-interval": "~0.1.3",
        "moment-timezone": "^0.5.0",
        "mongodb": "^2.2.10"
    },
    "description": "Light weight job scheduler for Node.js",
    "devDependencies": {
        "blanket": "1.1.5",
        "coveralls": "~2.11.4",
        "expect.js": "~0.3.1",
        "mocha": "~2.4.5",
        "mocha-lcov-reporter": "0.0.2",
        "q": "~1.4.1"
    },
    "directories": {},
    "dist": {
        "shasum": "251838119be5de6308a6f15c383f7bacc1ccb4f6",
        "tarball": "https://registry.npmjs.org/agenda/-/agenda-0.9.1.tgz"
    },
    "gitHead": "c64132e347240639a632f0f9ec83a3a54a020702",
    "homepage": "https://github.com/rschmukler/agenda#readme",
    "keywords": [
        "job",
        "jobs",
        "cron",
        "delayed",
        "scheduler",
        "runner"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "rschmukler",
            "email": "ryan@slingingcode.com"
        }
    ],
    "name": "agenda",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/rschmukler/agenda.git"
    },
    "scripts": {
        "test": "mocha"
    },
    "version": "0.9.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module agenda](#apidoc.module.agenda)
1.  [function <span class="apidocSignatureSpan">agenda.</span>job (args)](#apidoc.element.agenda.job)
1.  [function <span class="apidocSignatureSpan">agenda.</span>super_ ()](#apidoc.element.agenda.super_)
1.  object <span class="apidocSignatureSpan">agenda.</span>job.prototype

#### [module agenda.job](#apidoc.module.agenda.job)
1.  [function <span class="apidocSignatureSpan">agenda.</span>job (args)](#apidoc.element.agenda.job.job)

#### [module agenda.job.prototype](#apidoc.module.agenda.job.prototype)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>computeNextRunAt ()](#apidoc.element.agenda.job.prototype.computeNextRunAt)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>disable ()](#apidoc.element.agenda.job.prototype.disable)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>enable ()](#apidoc.element.agenda.job.prototype.enable)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>fail (reason)](#apidoc.element.agenda.job.prototype.fail)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>isRunning ()](#apidoc.element.agenda.job.prototype.isRunning)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>priority (priority)](#apidoc.element.agenda.job.prototype.priority)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>remove (cb)](#apidoc.element.agenda.job.prototype.remove)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>repeatAt (time)](#apidoc.element.agenda.job.prototype.repeatAt)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>repeatEvery (interval, options)](#apidoc.element.agenda.job.prototype.repeatEvery)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>run (cb)](#apidoc.element.agenda.job.prototype.run)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>save (cb)](#apidoc.element.agenda.job.prototype.save)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>schedule (time)](#apidoc.element.agenda.job.prototype.schedule)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>toJSON ()](#apidoc.element.agenda.job.prototype.toJSON)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>touch (cb)](#apidoc.element.agenda.job.prototype.touch)
1.  [function <span class="apidocSignatureSpan">agenda.job.prototype.</span>unique (unique, opts)](#apidoc.element.agenda.job.prototype.unique)



# <a name="apidoc.module.agenda"></a>[module agenda](#apidoc.module.agenda)

#### <a name="apidoc.element.agenda.job"></a>[function <span class="apidocSignatureSpan">agenda.</span>job (args)](#apidoc.element.agenda.job)
- description and source-code
```javascript
function Job(args) {
  args = args || {};

  // Remove special args
  this.agenda = args.agenda;
  delete args.agenda;

  // Process args
  args.priority = parsePriority(args.priority) || 0;

  // Set attrs to args
  var attrs = {};
  for (var key in args) {
    if (args.hasOwnProperty(key)) {
      attrs[key] = args[key];
    }
  }

  // Set defaults if undefined
  attrs.nextRunAt = attrs.nextRunAt || new Date();
  attrs.type = attrs.type || 'once';
  this.attrs = attrs;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.agenda.super_"></a>[function <span class="apidocSignatureSpan">agenda.</span>super_ ()](#apidoc.element.agenda.super_)
- description and source-code
```javascript
function EventEmitter() {
  EventEmitter.init.call(this);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.agenda.job"></a>[module agenda.job](#apidoc.module.agenda.job)

#### <a name="apidoc.element.agenda.job.job"></a>[function <span class="apidocSignatureSpan">agenda.</span>job (args)](#apidoc.element.agenda.job.job)
- description and source-code
```javascript
function Job(args) {
  args = args || {};

  // Remove special args
  this.agenda = args.agenda;
  delete args.agenda;

  // Process args
  args.priority = parsePriority(args.priority) || 0;

  // Set attrs to args
  var attrs = {};
  for (var key in args) {
    if (args.hasOwnProperty(key)) {
      attrs[key] = args[key];
    }
  }

  // Set defaults if undefined
  attrs.nextRunAt = attrs.nextRunAt || new Date();
  attrs.type = attrs.type || 'once';
  this.attrs = attrs;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.agenda.job.prototype"></a>[module agenda.job.prototype](#apidoc.module.agenda.job.prototype)

#### <a name="apidoc.element.agenda.job.prototype.computeNextRunAt"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>computeNextRunAt ()](#apidoc.element.agenda.job.prototype.computeNextRunAt)
- description and source-code
```javascript
computeNextRunAt = function () {
  var interval = this.attrs.repeatInterval;
  var timezone = this.attrs.repeatTimezone;
  var repeatAt = this.attrs.repeatAt;
  this.attrs.nextRunAt = undefined;

  if (interval) {
    computeFromInterval.call(this);
  } else if (repeatAt) {
    computeFromRepeatAt.call(this);
  }
  return this;

  function dateForTimezone (d) {
    d = moment(d);
    if(timezone) d.tz(timezone);
    return d;
  }

  function computeFromInterval() {
    var lastRun = this.attrs.lastRunAt || new Date();
    lastRun = dateForTimezone(lastRun);
    try {
      var cronTime = new CronTime(interval);
      var nextDate = cronTime._getNextDateFrom(lastRun);
      if (nextDate.valueOf() == lastRun.valueOf()) {
        // Handle cronTime giving back the same date for the next run time
        nextDate = cronTime._getNextDateFrom(dateForTimezone(new Date(lastRun.valueOf() + 1000)));
      }
      this.attrs.nextRunAt = nextDate;
    } catch (e) {
      // Nope, humanInterval then!
      try {
        if (!this.attrs.lastRunAt && humanInterval(interval)) {
          this.attrs.nextRunAt = lastRun.valueOf();
        } else {
          this.attrs.nextRunAt = lastRun.valueOf() + humanInterval(interval);
        }
      } catch (e) {}
    } finally {
      if (isNaN(this.attrs.nextRunAt)) {
        this.attrs.nextRunAt = undefined;
        this.fail('failed to calculate nextRunAt due to invalid repeat interval');
      }
    }
  }

  function computeFromRepeatAt() {
    var lastRun = this.attrs.lastRunAt || new Date();
    var nextDate = date(repeatAt).valueOf();

    var offset = Date.now();  // if you do not specify offset date for below test it will fail for ms
    if (offset === date(repeatAt,offset).valueOf()) {
      this.attrs.nextRunAt = undefined;
      this.fail('failed to calculate repeatAt time due to invalid format');
    } else if (nextDate.valueOf() == lastRun.valueOf()) {
      this.attrs.nextRunAt = date('tomorrow at ', repeatAt);
    } else {
      this.attrs.nextRunAt = date(repeatAt);
    }
  }
}
```
- example usage
```shell
...
  var self = this,
      agenda = self.agenda,
      definition = agenda._definitions[self.attrs.name];

  var setImmediate = setImmediate || process.nextTick;
  setImmediate(function() {
    self.attrs.lastRunAt = new Date();
    self.computeNextRunAt();
    self.save(function() {
      var jobCallback = function(err) {
if (err) {
  self.fail(err);
}

self.attrs.lastFinishedAt = new Date();
...
```

#### <a name="apidoc.element.agenda.job.prototype.disable"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>disable ()](#apidoc.element.agenda.job.prototype.disable)
- description and source-code
```javascript
disable = function () {
  this.attrs.disabled = true;
  return this;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.agenda.job.prototype.enable"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>enable ()](#apidoc.element.agenda.job.prototype.enable)
- description and source-code
```javascript
enable = function () {
  this.attrs.disabled = false;
  return this;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.agenda.job.prototype.fail"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>fail (reason)](#apidoc.element.agenda.job.prototype.fail)
- description and source-code
```javascript
fail = function (reason) {
  if(reason instanceof Error) {
    reason = reason.message;
  }
  this.attrs.failReason = reason;
  this.attrs.failCount = (this.attrs.failCount || 0) + 1;
  this.attrs.failedAt = new Date();
  return this;
}
```
- example usage
```shell
...
Sets 'job.attrs.failedAt' to 'now', and sets 'job.attrs.failReason'
to 'reason'.

Optionally, 'reason' can be an error, in which case 'job.attrs.failReason' will
be set to 'error.message'

'''js
job.fail('insuficient disk space');
// or
job.fail(new Error('insufficient disk space'));
job.save();
'''

### run(callback)
...
```

#### <a name="apidoc.element.agenda.job.prototype.isRunning"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>isRunning ()](#apidoc.element.agenda.job.prototype.isRunning)
- description and source-code
```javascript
isRunning = function () {
  if (!this.attrs.lastRunAt) return false;
  if (!this.attrs.lastFinishedAt) return true;
  if (this.attrs.lockedAt && this.attrs.lastRunAt.getTime() > this.attrs.lastFinishedAt.getTime()) {
    return true;
  }
  return false;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.agenda.job.prototype.priority"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>priority (priority)](#apidoc.element.agenda.job.prototype.priority)
- description and source-code
```javascript
priority = function (priority) {
  this.attrs.priority = parsePriority(priority);
  return this;
}
```
- example usage
```shell
...

### priority(priority)

Specifies the 'priority' weighting of the job. Can be a number or a string from
the above priority table.

'''js
job.priority('low');
job.save();
'''

### unique(properties, [options])

Ensure that only one instance of this job exists with the specified properties
...
```

#### <a name="apidoc.element.agenda.job.prototype.remove"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>remove (cb)](#apidoc.element.agenda.job.prototype.remove)
- description and source-code
```javascript
remove = function (cb) {
  // refactored NF 21/04/2015
  this.agenda.cancel( {_id: this.attrs._id}, cb );
<span class="apidocCodeCommentSpan">/*
  var self = this;
  this.agenda._db.remove({_id: this.attrs._id}, function(err, count) {
    if(err) {
      return cb(err);
    }
    cb(err, count);
  });
*/
</span>}
```
- example usage
```shell
...
// or pass additional connection options:
// var agenda = new Agenda({db: {address: mongoConnectionString, collection: "jobCollectionName", options: {server:{auto_reconnect
:true}}}});

// or pass in an existing mongodb-native MongoClient instance
// var agenda = new Agenda({mongo: myMongoClient});

agenda.define('delete old users', function(job, done) {
User.remove({lastLogIn: { $lt: twoDaysAgo }}, done);
});

agenda.on('ready', function() {
agenda.every('3 minutes', 'delete old users');

// Alternatively, you could also do:
agenda.every('*/3 * * * *', 'delete old users');
...
```

#### <a name="apidoc.element.agenda.job.prototype.repeatAt"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>repeatAt (time)](#apidoc.element.agenda.job.prototype.repeatAt)
- description and source-code
```javascript
repeatAt = function (time) {
  this.attrs.repeatAt = time;
  return this;
}
```
- example usage
```shell
...
'''

### repeatAt(time)

Specifies a 'time' when the job should repeat. [Possible values](https://github.com/matthewmueller/date#examples)

'''js
job.repeatAt('3:30pm');
job.save();
'''

### schedule(time)

Specifies the next 'time' at which the job should run.
...
```

#### <a name="apidoc.element.agenda.job.prototype.repeatEvery"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>repeatEvery (interval, options)](#apidoc.element.agenda.job.prototype.repeatEvery)
- description and source-code
```javascript
repeatEvery = function (interval, options) {
  options = options || {};
  this.attrs.repeatInterval = interval;
  this.attrs.repeatTimezone = options.timezone ? options.timezone : null;
  return this;
}
```
- example usage
```shell
...
  agenda.start();
});
'''

'''js
agenda.on('ready', function() {
  var weeklyReport = agenda.create('send email report', {to: 'another-guy@example.com'})
  weeklyReport.repeatEvery('1 week').save();
  agenda.start();
});
'''

# Full documentation

Agenda's basic control structure is an instance of an agenda. Agenda's are
...
```

#### <a name="apidoc.element.agenda.job.prototype.run"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>run (cb)](#apidoc.element.agenda.job.prototype.run)
- description and source-code
```javascript
run = function (cb) {
  var self = this,
      agenda = self.agenda,
      definition = agenda._definitions[self.attrs.name];

  var setImmediate = setImmediate || process.nextTick;
  setImmediate(function() {
    self.attrs.lastRunAt = new Date();
    self.computeNextRunAt();
    self.save(function() {
      var jobCallback = function(err) {
        if (err) {
          self.fail(err);
        }

        self.attrs.lastFinishedAt = new Date();
        self.attrs.lockedAt = null;
        self.save(function(saveErr, job) {
          cb && cb(err || saveErr, job);
          if (err) {
            agenda.emit('fail', err, self);
            agenda.emit('fail:' + self.attrs.name, err, self);
          } else {
            agenda.emit('success', self);
            agenda.emit('success:' + self.attrs.name, self);
          }
          agenda.emit('complete', self);
          agenda.emit('complete:' + self.attrs.name, self);
        });
      };

      try {
        agenda.emit('start', self);
        agenda.emit('start:' + self.attrs.name, self);
        if (!definition) {
          throw new Error('Undefined job');
        }
        if (definition.fn.length === 2) {
          definition.fn(self, jobCallback);
        } else {
          definition.fn(self);
          jobCallback();
        }
      } catch (e) {
        jobCallback(e);
      }
    });
  });
}
```
- example usage
```shell
...

### run(callback)

Runs the given 'job' and calls 'callback(err, job)' upon completion. Normally
you never need to call this manually.

'''js
job.run(function(err, job) {
  console.log("I don't know why you would need to do this...");
});
'''

### save(callback)

Saves the 'job.attrs' into the database.
...
```

#### <a name="apidoc.element.agenda.job.prototype.save"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>save (cb)](#apidoc.element.agenda.job.prototype.save)
- description and source-code
```javascript
save = function (cb) {
  this.agenda.saveJob(this, cb);
  return this;
}
```
- example usage
```shell
...
  agenda.start();
});
'''

'''js
agenda.on('ready', function() {
  var weeklyReport = agenda.create('send email report', {to: 'another-guy@example.com'})
  weeklyReport.repeatEvery('1 week').save();
  agenda.start();
});
'''

# Full documentation

Agenda's basic control structure is an instance of an agenda. Agenda's are
...
```

#### <a name="apidoc.element.agenda.job.prototype.schedule"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>schedule (time)](#apidoc.element.agenda.job.prototype.schedule)
- description and source-code
```javascript
schedule = function (time) {
  this._scheduled = true;
  this.attrs.nextRunAt = (time instanceof Date) ? time : date(time);
  return this;
}
```
- example usage
```shell
...
  from: 'example@example.com',
  subject: 'Email Report',
  body: '...'
}, done);
});

agenda.on('ready', function() {
agenda.schedule('in 20 minutes', 'send email report', {to: 'admin@example.com'});
agenda.start();
});
'''

'''js
agenda.on('ready', function() {
var weeklyReport = agenda.create('send email report', {to: 'another-guy@example.com'})
...
```

#### <a name="apidoc.element.agenda.job.prototype.toJSON"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>toJSON ()](#apidoc.element.agenda.job.prototype.toJSON)
- description and source-code
```javascript
toJSON = function () { // create a persistable Mongo object -RR
    var self = this,
        attrs = self.attrs || {};

    var result = {};

    for (var prop in attrs) {
      if (attrs.hasOwnProperty(prop)) {
        result[prop] = attrs[prop];
      }
    }

    var dates = ['lastRunAt', 'lastFinishedAt', 'nextRunAt', 'failedAt', 'lockedAt'];
    dates.forEach(function(d) {
      if (result[d]) {
        result[d] = new Date(result[d]);
      }
    });

    return result;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.agenda.job.prototype.touch"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>touch (cb)](#apidoc.element.agenda.job.prototype.touch)
- description and source-code
```javascript
touch = function (cb) {
  this.attrs.lockedAt = new Date();
  this.save(cb);
}
```
- example usage
```shell
...

Resets the lock on the job. Useful to indicate that the job hasn't timed out
when you have very long running jobs.

'''js
agenda.define('super long job', function(job, done) {
doSomeLongTask(function() {
  job.touch(function() {
    doAnotherLongTask(function() {
      job.touch(function() {
        finishOurLongTasks(done);
      });
    });
  });
});
...
```

#### <a name="apidoc.element.agenda.job.prototype.unique"></a>[function <span class="apidocSignatureSpan">agenda.job.prototype.</span>unique (unique, opts)](#apidoc.element.agenda.job.prototype.unique)
- description and source-code
```javascript
unique = function (unique, opts) {
  this.attrs.unique = unique;
  this.attrs.uniqueOpts = opts;
  return this;
}
```
- example usage
```shell
...

'options' is an optional argument which can overwrite the defaults. It can take
the following:

- 'insertOnly': 'boolean' will prevent any properties from persisting if job already exists. Defaults to false.

'''js
job.unique({'data.type': 'active', 'data.userId': '123', nextRunAt(date)});
job.save();
'''

### fail(reason)

Sets 'job.attrs.failedAt' to 'now', and sets 'job.attrs.failReason'
to 'reason'.
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

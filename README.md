# Zig Datetime

[![Build Status](https://travis-ci.org/frmdstryr/zig-datetime.svg?branch=master)](https://travis-ci.org/frmdstryr/zig-datetime)

A datetime module for Zig with an api similar to python's Arrow.

> NOTE: This does not implement DST.


```zig

const allocator = std.heap.page_allocator;
var date = try Date.create(2019, 12, 25);
var next_year = date.shiftDays(7);
assert(next_year.year == 2020);
assert(next_year.month == 1);
assert(next_year.day == 1);

// In UTC
var now = Datetime.now();
var now_str = try now.formatHttp(allocator);
defer allocator.free(now_str);
std.debug.warn("The time is now: {}\n", .{now_str});
// The time is now: Fri, 20 Dec 2019 22:03:02 UTC


```

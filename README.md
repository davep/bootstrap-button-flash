# Bootstrap/Chrome/LastPass button fade issue

Recently I upgraded my copy of Chrome to 69 (from 63). After doing so the
application I was working on (Django, Bootstrap, etc) started to show an odd
problem: buttons styled with Bootstrap's "btn" class would fade in. This was
most noticeable with those that had a solid colour (so `btn-primary`, for
example).

The thing was, this wasn't on every page. Some pages were fine. After
narrowing things down a little I found that any page that had a script lower
down the page *didn't* display the problem. This, in turn, resulted in me
finding that if I added this:

```html
<script></script>
```

to the bottom of every `body`, the problem went away!

That was just a curious workaround, of course. It wasn't a solution.

After some ore digging I finally narrowed it down to there being a
combination of a `form` and Bootstrap buttons on the same page. The
resulting [`index.html`](index.html) which you'll find in this repo is the
minimal version of the problem.

What I've since found is that it's fine in Incognito mode; this would
suggest that it's an issue that also involves one of the extensions I have
loaded. A process of elimination has narrowed it down to LastPass.

So.... if I have Chrome 69 (tested on GNU/Linux and macOS), and Bootstrap 4,
and a form, and a Bootstrap button, and no script in the body of the page,
and I have the LastPass extension loaded.... buttons oddly fade their colour
in every time the page loads.

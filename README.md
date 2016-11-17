# CSS Can Be Easy

This guide is to teach that building responsive sites and applications using CSS can be easier than you might think.
There are a few best practices

## Assumptions

This guide is built around a support stack of IE 11 and modern browsers (evergreen Chrome, Edge, Safari, Firefox, Opera).
IE <11 is no longer supported by Microsoft for even security updates.
This means not only is your team missing out on awesome features like `calc` and flexbox, but continuing to support IE <11 puts your app and more importantly your customers at risk.
To read more about Microsoft's support policy, see: https://www.microsoft.com/en-us/WindowsForBusiness/End-of-IE-support.

This recommendation guide pretty heavily uses `display: flex`.
Even with the support stack listed above, I would recommend using something like [autoprefixer](https://github.com/postcss/autoprefixer) to fill in gaps in prefixing or experimental features.

Also, while most everything here should Just Work™, there are a few known flexbox bugs.
To learn more about these, check out the popular [Flexbugs Repo](https://github.com/philipwalton/flexbugs).

## Let's Get Started!

1. [Box Model](01-box-model.md)
2. [Resets](02-resets.md)
2. [Components vs Layout](03-components-vs-layout.md)
3. [Grids (the Easy Way)](04-grids.md)

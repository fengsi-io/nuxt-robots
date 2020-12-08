# nuxt-robots

## Setup

1. Add `nuxt-robots` dependency to your project

```bash
yarn add nuxt-robots # or npm install nuxt-robots
```

2. Add `nuxt-robots` to the `modules` section of `nuxt.config.js`

```js
export default {
  modules: [
    // Simple usage
    'nuxt-robots',

    // With options
    ['nuxt-robots', { 
      /* module options */
      cacheTime: 1000 * 60 * 10,
      robots: () => {
        return []
      }
    }]
  ]
}
```

### Using top level options

```js
export default {
  modules: [
    'nuxt-robots'
  ],
  robots: {
    /* module options */
    cacheTime: 1000 * 60 * 10,
    robots: () => {
      return []
    }
  }
}
```
### cache time

default 1000 * 60 * 10 s

## Options

The module option parameter can be:

### `Object`

```js
export default {
  robots: {
    UserAgent: '*',
    Disallow: '/'
  }
}
```

### `Array`

```js
export default {
  robots: [
    {
      UserAgent: 'Googlebot',
      Disallow: () => '/users' // accepts function
    }
  ]
}
```

### `Function`

```js
export default {
  robots: () => {
    return {
      UserAgent: '*',
      Disallow: '/'
    }
  }
}
```

### Will generate a /robots.txt

```bash
User-agent: Googlebot
Disallow: /users
User-agent: Bingbot
Disallow: /admin
```

### The keys and values available:

- UserAgent = `User-agent`
- CrawlDelay = `Crawl-delay`
- Disallow = `Disallow`
- Allow = `Allow`
- Host = `Host`
- Sitemap = `Sitemap`
- CleanParam = `Clean-param`

**Note:** Don't worry keys are parsed with case insensitive and special characters.

The original link [@nuxtjs/robots](https://github.com/wusongliang/robots-module)

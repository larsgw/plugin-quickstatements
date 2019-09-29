## Install

Add the following line to your `~/.npmrc`:

```
@egonw:registry=https://npm.pkg.github.com
```

And then run:

```shell
npm install @egonw/plugin-quickstatements
```

To run the below example, you also need to install a few other packages
(as they are currently not automatically pulled in, it seems):

```shell
npm install @citation-js/core
npm install @citation-js/plugin-pubmed
npm install @citation-js/plugin-doi
npm install @babel/register
npm install @babel/core
```


## Use

Install the plugin by `require`-ing it:

```js
require('@citation-js/plugin-quickstatements')
```

## Formats

Formats and other features added by this plugin.

### Input

The input is CSL generated by citation.js by any of its supported formats.
Here's an example for how to create QuickStatements for a PubMed Central
identifier:

```javascript
c = require('@citation-js/core')
require('@citation-js/plugin-pubmed')
require('@citation-js/plugin-doi')

require('@babel/register')
require('./src')

c.Cite.async([
  '10.1186/s13321-019-0380-5',
  'pmid:14266813',
  'PMC6613236'
])
  .then(Cite =>
    console.log(Cite.format('quickstatements'))
  )
  .catch(console.error)
```

### Output

The output is [QuickStatements]() to be copied
into the [online webservice](). The output
looks like:

```
	CREATE

	LAST	P31	Q13442814
	LAST	Len	"Journal of Cheminformatics, ORCID, and GitHub"
	LAST	P304	"44"
	LAST	P356	"10.1186/s13321-019-0365-4"
	LAST	P433	"1"
	LAST	P478	"11"
	LAST	P698	"31281945"
	LAST	P932	"PMC6613236"
	LAST	P1476	"Journal of Cheminformatics, ORCID, and GitHub"
	LAST	P577	"2019-07-08"
	LAST	P2093	"Egon Willighagen"	P1545	"1"	
	LAST	P2093	"Nina Jeliazkova"	P1545	"2"	
	LAST	P2093	"Rajarshi Guha"	P1545	"3"
```

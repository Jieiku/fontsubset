# FontSubset

This project uses the [subset-font library](https://www.npmjs.com/package/subset-font)

The fontsubset.js file originally comes from [saurori](https://github.com/omacranger/fontawesome-subset/issues/16#issuecomment-1151744198)

I created/extended:

- the readme
- directory structure
- package.json
- extended fontsubset.js to accept parameters so that multiple subsets can be defined.
- extended fontsubset.js to create output directories if they do not exist.

Setup is Quick and Easy:

```shell
git clone https://github.com/Jieiku/fontsubset
cd fontsubset
npm install fs path glob yaml subset-font
npm install --save-dev @fortawesome/fontawesome-free
```

The subsets are defined in package.json, there are two defined subsets abridge and abridge-full

When you run the below commands, they will run the `abridge` and `abridge-full` scripts defined in the `package.json` file, these lines are what determine what icons will be included in the output font.

```shell
npm run-script abridge
npm run-script abridge-full
```

The above two run-script commands will generate the new fonts and output them to the assets folder, you will find these commands defined in the `package.json` file.
To add new icons to either of these two subsets you need to edit the `package.json` file and add more icons to the command, or even add a new subset script entry of your own.

### package.json:
```json
"abridge": "node fontsubset.js abridge magnifying-glass circle-half-stroke angle-up angles-left angle-left angle-right angles-right",
"abridge-full": "node fontsubset.js abridge-full magnifying-glass circle-half-stroke angle-up angles-left angle-left angle-right angles-right tags layer-group book circle-info calendar glasses circle-dollar-to-slot"
```

The script will output various formats, but the one your probably after is the woff2, the fonts will be output to the assets folder.

My original motivation was for my Zola theme [Abridge](https://abridge.netlify.app/)

The most common way to use these fonts is with a css file, you can use the one from the Abridge Theme as an example:

https://github.com/Jieiku/abridge/blob/master/sass/fonts/_Abridge.scss

You can also see it in use on the [Abridge Demo](https://abridge.netlify.app/) but the css there is minified of coarse.

It should also be possible to use the css files from Font Awesome itself, but for my small subset of icons this was all that I needed, it is a somewhat modified version of the css file normally generated by fontello.

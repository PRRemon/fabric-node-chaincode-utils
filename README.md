[![Build Status](https://travis-ci.org/wearetheledger/fabric-node-chaincode-utils.svg?branch=master)](https://travis-ci.org/wearetheledger/fabric-node-chaincode-utils) [![Greenkeeper badge](https://badges.greenkeeper.io/wearetheledger/fabric-node-chaincode-utils.svg)](https://greenkeeper.io/) [![npm version](https://badge.fury.io/js/%40theledger%2Ffabric-chaincode-utils.svg)](https://badge.fury.io/js/%40theledger%2Ffabric-chaincode-utils)
# fabric-node-chaincode-utils
A Nodejs module that helps you build your Hyperledger Fabric nodejs chaincode. Testing is done using the [fabric-mock-stub](https://github.com/wearetheledger/fabric-mock-stub).

- [docs](https://wearetheledger.github.io/fabric-node-chaincode-utils)
- [example usage](https://github.com/wearetheledger/fabric-network-boilerplate/tree/master/chaincode/node)

## Table of contents
- [Installation](#installation)
- [Writing chaincode](https://github.com/wearetheledger/fabric-node-chaincode-utils/wiki/Writing-chaincode)
- [Changes](#changes)
- [Contributing](#contributing)
- [Credits](#credits)
- [License](#license)

## Installation 
```sh
yarn add @theledger/fabric-chaincode-utils
```

## Changes

### v2.0.0 - BREAKING
- Objects parsed as multiple arguments, should now only be passed as a JSON object in 1 argument.

**before**
```
["function","prop1","prop2"]
```

```javascript
const verifiedArgs = await Helpers.checkArgs<{ prop1: string, prop2: string }>(args, Yup.object()
            .shape({
                prop1: Yup.string().required(),
                prop2: Yup.string().required(),
            }));
```

**after**
```
["function","{\"prop1\":\"prop1\",\"prop2\":\"prop2\"}"]
```

```javascript
const verifiedArgs = await Helpers.checkArgs<{ prop1: string, prop2: string }>(args[0], Yup.object()
            .shape({
                prop1: Yup.string().required(),
                prop2: Yup.string().required(),
            }));
```

## Contributing
 
1. Fork it! 🍴
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request 😁 🎉

## Credits

- [@Kunstmaan](https://github.com/Kunstmaan/hyperledger-fabric-node-chaincode-utils) for the initial idea and part of the util code.
- Developer - Jo ([@jestersimpps](https://github.com/jestersimpps))
- Developer - Jonas ([@Superjo149](https://github.com/Superjo149))
- Company - TheLedger ([theledger.be](https://theledger.be))

## License
The MIT License (MIT)

Copyright (c) 2018 TheLedger

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

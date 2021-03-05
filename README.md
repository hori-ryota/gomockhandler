# gomockhandler

gomockhandler is a simple wrapper of [mockgen](https://github.com/golang/mock).

- You can use the same options as mockgen to generate mocks.
- You can check if mock is up to date.
- [optional] You can manage your mocks in one config file.

## Install

Note: You have to install `mockgen` first.

**TBD**

## How to use

### Generate mock

You can use the same options as mockgen to generate mocks.

Example:
```
gomockhandler -source=foo.go [other options]
```

See [golang/mock#running-mockgen](https://github.com/golang/mock#running-mockgen) for more information.

### Check if mock is up-to-date

You can check if mock is up to date with `-check true` flag.

```
gomockhandler -check true -source=foo.go [other options]
```

### [optional] manage all mocks on one config

**TBD**

## Project status

- [ ] can generate mocks with the same options as mockgen.
  - [x] [Source mode](https://github.com/golang/mock#source-mode)
  - [ ] [Reflect mode](https://github.com/golang/mock#reflect-mode)
- [ ] can check if mock is up to date.
  - [x] check by comparing.
  - [ ] check by checking `gomockhandler.json`(in order to detect deletion of the original interface).
- [ ] can manage all mocks in one config file. 
  - [ ] create mocks from the config file.

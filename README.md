![Action Validation](https://github.com/betty-services/Remote-Model-Helper-Steps-Custom-Action-Functions/actions/workflows/main.yml/badge.svg?event=push)

# Remote Model Helper Steps Custom Action Functions

This repository hosts the code for the custom actions steps found in the [Remote Model Helper Steps](https://my.bettyblocks.com/block-store/5d08f9d6-5332-4553-8e86-61f527d6a085) from the Betty Blocks block store.

## This repository hosts the following steps:

- Add IDS
- Dissect Params
- Fix Property Type
- Get Fields
- Get filters
- Get Limit Offset
- Parse as JWT
- Provision Fields

### Add IDS

This step takes an `array` as it's input, and expects it to have elements of the type `object` inside of it.

It will continue to add the `id` key to every `object` element in it. You can specify the value that it should get from another key in the `object`, or it will automatically add the value starting at `1` and counting up from there.

### Dissect Params

This step takes the `params` object that a remote model action has as it's input and 'dissects' it into 4 other variables:

- Fields
- Filters
- Offset
- Limit

#### Fields

The Data API tells us which fields are required to be returned to the front-end. This variable will most-likely be used for the `provision fields` step in this repository.

#### Filters

This returns the filters set on the Remote Data Model on the front-end, e.g. `name equals 'maarten'`. It flattens the data into a simple object such as:

```
{
    name: 'maarten'
}
```

#### Offset

Offset is the beginning number of the records to show.
So when we have a datatable that is on the first page, and shows 5 records, the offset will be `0`. If proceed to go to the next page, the offset will be `5`.

#### Limit

Limit is the end number of the records to show.
So when we have a datatable that is on the first page, and that shows 5 records, the limit will be `5`. If proceed to go to the next page, the limit will be `10`.

### Fix Property Type

This step lets you convert values to and from numbers.
This step takes either an `object` or `array` as an input, alongside the `keyname` that should be converted.
**If the value you're trying to convert is `foo` and you want to convert it to a number, it will result in `NaN` so you better make sure the value can be converted!**

### Parse as JWT

This step takes in a JWT as input and lets you decode all it's information into readable variables to use in the Betty Blocks Action IDE.

### Provision Fields

This step takes the `fields` from the `Dissect params` object, alongside an input of an `Array` of `Object` and will add any missing `keys` in the input.

### Get Fields

Does the same as the `disect params` step but is only limited to the field.

### Get Filters

Does the same as the `disect params` step but is only limited to the fitlers **and** doesn't flatten the object.

### Get Limit and Offset

Does the same as the `disect params` step but is only limited to the limit and offset.

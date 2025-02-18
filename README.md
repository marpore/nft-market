# nft-market

[![PyPI version](https://badge.fury.io/py/nft-market.svg)](https://badge.fury.io/py/nft-market)
[![test](https://github.com/ukaznil/nft-market/actions/workflows/pytest.yml/badge.svg)](https://github.com/ukaznil/nft-market/actions/workflows/pytest.yml)

## What is it?

**nft-market** is a Python library by which current market information of NFTs on several famous NFT markets (OpenSea,
Tofu, PancakeSwap, etc) can be obtained.

## Main features

**nft-market** provides simple APIs that return market information just by your giving the following arguments.

- The marketplace (from `nft_market.Market`)
- the ID of a specific NFT (See the below in detail.)

```python
from nft_market import Market, Retriever

r = Retriever()
print(r.fetch(Market.OpenSea, 'boredapeyachtclub'))  # Bored Ape Yacht Club

# [Output]
# type: nft_market.NFTInfo
# NFTInfo(name='boredapeyachtclub', num_items_all=None, num_listing=10000, num_owners=6400, floor=110.0, volume=487100.0)
```

### Currently supported marketplaces

At this moment, the following marketplaces are supported in **nft-market**.

- [OpenSea](https://opensea.io/)
- [Entrepot](https://entrepot.app/)
- [Tofu](https://tofunft.com/)
- [PancakeSwap](https://pancakeswap.finance/nfts)
- [Rarible](https://rarible.com/)
- [GhostMarket](https://ghostmarket.io/)

Other marketplaces will be added into the list in the future. You can, off course, request them in issues if needed
immediately. Either PRs or issues are always welcome!

### How to get the ID of a NFT?

Although it depends on which marketplace you use, you can basically find it in the URL.

#### Example 1: OpenSea

When you want to retrieve the information of the NFT of [Bored Ape Yacht Club
](https://opensea.io/collection/boredapeyachtclub), the URL looks like `https://opensea.io/collection/boredapeyachtclub`
. In this URL, what differs according to a NFT is the part of `boredapeyachtclub`, which is all you need to use **
nft-market**.

#### Example 2: Tofu

URLs look like `https://tofunft.com/collection/astardegens/items`. In this case, what **nft-market** requires is only
the part of `astardegens`.

#### Other examples

We have several examples of the usage in [samples.py](https://github.com/ukaznil/nft-market/blob/master/samples.py) for
references.

### Available information

What you can retrieve may change by a marketplace you specify, as follows.

| Market      | Name    | # Items | # Listing | # Owners | Floor   | Volume  |
|-------------|---------|---------|-----------|----------|---------|---------|
| OpenSea     | &check; |         | &check;   | &check;  | &check; | &check; |
| Entrepot    | &check; |         | &check;   |          | &check; | &check; |
| Tofu        | &check; |         | &check;   |          | &check; | &check; |
| PancakeSwap | &check; | &check; | &check;   |          | &check; | &check; |
| Rarible     | &check; | &check; |           | &check;  | &check; | &check; |
| GhostMarket | &check; | &check; |           | &check;  | &check; | &check; |   

Other information may be provided in the future!

## Installation

You can install **nft-market** by pip.

```shell
$ pip install nft-market
```

Also, as **nft-market** depends on Firefox and its driver, you need to install them.

```shell
[mac]
$ brew install firefox

[ubuntu]
$ sudo apt install firefox
```

Besides, all Python dependencies are listed up in `requirements.txt`. Please install them
by `$ pip install -r requirements.txt` if you install **nft-market** not by pip but by cloning from GitHub.
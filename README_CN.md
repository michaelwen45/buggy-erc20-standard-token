

# Awesome-buggy-erc20-tokens
[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Join the chat at https://gitter.im/sec-bit/Lobby](https://badges.gitter.im/sec-bit/Lobby.svg)](https://gitter.im/sec-bit/Lobby)
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

以太坊 ERC20 智能合约风险问题及影响 Token 汇总

## ERC20 Token 面临的主要问题

以太坊 ERC20 Token 标准自 2015 年 11 月 19 日诞生以来[1]，为智能合约、以太坊生态以及区块链应用的发展产生了巨大的贡献。据 Etherscan 网站[数据显示](https://etherscan.io/tokens)，截止 2018 年 6 月 20 日，以太坊主网上 ERC20 Token 数量已超过 90000。下图是我们统计的 ERC20 每日创建数量趋势图。

![以太坊主网上 ERC20 合约每日创建数量](img/erc20-creation.jpeg)

ERC20 Token 在其发展历程中，经历了逐渐成熟和完善的过程。其中有不少 ERC20 智能合约出现过重大漏洞，造成难以估量的经济损失[2-5]。

此外，很多 Token 合约未参照 ERC20 标准实现，也给 DApp 开发带来很大的困扰[6-7]。

在此，我们对已知的漏洞和缺陷做了一个汇总，收录的 Token 问题类型主要包括：

1. Token 合约安全漏洞
2. 不符合 ERC20 规范导致的兼容问题
3. Token 合约管理员的权限过高

## 为何要维护一个 token list

+ 列出常见的智能合约漏洞，为合约开发者提供学习细节素材
+ 列出问题 Token 合约，为基于 ERC20 的 DApp 开发者提供参考，提前规避问题 Token 引入的潜在安全风险
+ 便于交易所、项目方及 Token 投资者能够便利地查询到问题 Token，避免在交易中造成损失

## 项目主要包含内容

+ 常见安全漏洞描述
+ 已部署的漏洞合约 Token 列表
+ 不兼容的合约 Token 列表

## 项目各部分说明

```bash
awesome-buggy-erc20-tokens
├── TOKEN_DETAIL_DICT.json
├── bug-list.md
├── issues.json
├── badtop600token.csv
├── badtop600token.json
├── raw
├── csv
├── json
└── gen_list_from_raw.py
```

- [`TOKEN_DETAIL_DICT.json`](TOKEN_DETAIL_DICT.json) 收集了被 [CoinMarketCap](https://coinmarketcap.com/tokens/) 收录的 ERC20 合约主网地址和基本信息
- [`bug-list.md`](bug-list.md) 包含已知漏洞的详细描述
- [`issues.json`](issues.json) 是已知漏洞和代号编码的映射
- [`bad_top_tokens.csv`](bad_top_tokens.csv) 和 [`bad_top_tokens.json`](bad_top_tokens.json) 是问题 Token 的汇总列表，分别以 CSV 和 JSON 形式展示
- [`raw`](raw)、[`csv`](csv) 和 [`json`](json) 文件夹是各已知漏洞和受影响的合约地址，分别以纯文本、CSV、JSON 形式展示
- [`gen_list_from_raw.py`](gen_list_from_raw.py) 是生成各个 CSV 和 JSON 列表的脚本

如下所示，CSV 和 JSON 格式的列表，可以帮助开发者快速浏览和查询某合约地址存在哪些已知问题。

```csv
addr,category,name,symbol,info
0x093e5C256Ff8B32c7F1377f4C20e331674C77F00,[7],Dignity,DIG,_
0x0aeF06DcCCC531e581f0440059E6FfCC206039EE,[1],Intelligent Trading Technologies,ITT,_
0x0b76544F6C413a555F309Bf76260d1E02377c02A,[1][12][14][7],Internet Node Token,INT,_
```

```json
{
    "0x093e5C256Ff8B32c7F1377f4C20e331674C77F00": {
        "info": "_",
        "issues": {
            "totalsupply-overflow": true
        },
        "name": "Dignity",
        "rank": 613,
        "symbol": "DIG"
    },
    "0x0aeF06DcCCC531e581f0440059E6FfCC206039EE": {
        "info": "_",
        "issues": {
            "transfer-no-retrun": true
        },
        "name": "Intelligent Trading Technologies",
        "rank": 551,
        "symbol": "ITT"
    },
    "0x0b76544F6C413a555F309Bf76260d1E02377c02A": {
        "info": "_",
        "issues": {
            "owner-control-sell-price-for-overflow": true,
            "owner-decrease-balance-by-mint-by-overflow": true,
            "totalsupply-overflow": true,
            "transfer-no-retrun": true
        },
        "name": "Internet Node Token",
        "rank": 168,
        "symbol": "INT"
    }
}
```

## 如何参与贡献

我们希望通过此项目为以太坊生态做出一点贡献。

我们会长期维护此列表，并对其进行持续地更新。也欢迎大家共同参与进来，共同推进以太坊生态健康发展。

目前我们仅收录在 CoinMarketCap 有过市值显示的 Token 合约。如果你觉得我们有所遗漏，欢迎编辑 [`TOKEN_DETAIL_DICT.json`](TOKEN_DETAIL_DICT.json) 文件添加。

如果你发现了我们未收录的漏洞，欢迎按照以下流程贡献更新：

- 在 [`bug-list.md`](bug-list.md) 文件中添加漏洞名称和描述，附上引用出处地址
- 在 [`raw`](raw) 文件夹中创建以漏洞名称命名的新文件，填入受影响的合约地址
- 在 [`issues.json`](issues.json) 中增加新漏洞的名称和序列号
- 在项目根目录运行 `python3 gen_list_from_raw.py -i raw/* -o bad_top_tokens`
- 检查更改的文件，提交更新

如果你有其他任何问题或者想法，欢迎加入我们的 [Gitter](https://gitter.im/sec-bit/Lobby) 参与讨论。

## Reference

- [1] [ERC-20 Token Standard](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md), 
Nov 19, 2015
- [2] [Understanding The DAO Hack for Journalists](https://medium.com/@pullnews/understanding-the-dao-hack-for-journalists-2312dd43e993), Jun 19, 2016
- [3] [A disastrous vulnerability found in smart contracts of BeautyChain (BEC)](https://medium.com/secbit-media/a-disastrous-vulnerability-found-in-smart-contracts-of-beautychain-bec-dbf24ddbc30e), Apr 23, 2018
- [4] [Alert! Another integer overflow vulnerability just found in HXG smart contract](https://medium.com/secbit-media/alert-another-integer-overflow-vulnerability-just-found-in-hxg-smart-contract-ff2f69fdd242), May 19, 2018
- [5] [Bugged Smart Contract FuturXE: How Could Someone Mess up with Boolean? (CVE-2018–12025)](https://medium.com/secbit-media/bugged-smart-contract-f-e-how-could-someone-mess-up-with-boolean-d2251defd6ff), Jun 6, 2018
- [6] [An Incompatibility in Ethereum Smart Contract Threatening dApp Ecosystem](https://medium.com/loopring-protocol/an-incompatibility-in-smart-contract-threatening-dapp-ecosystem-72b8ca5db4da), Jun 8, 2018
- [7] [Redundant Check in ERC20 Smart Contracts’ approve()](https://medium.com/secbit-media/redundant-check-in-erc20-smart-contracts-approve-5a675bb88261), Jun 15, 2018

## 版权声明

[GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.en.html)
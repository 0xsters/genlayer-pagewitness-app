# PageWitness App

The web frontend for the **PageWitness** Intelligent Contract on GenLayer.

PageWitness answers questions about what a public web page actually says, with the answer decided by validator consensus and backed by a verbatim quote from the page. Anyone registers a page URL and one plain-language question (a deadline, an eligibility rule, a price, a requirement). When the question is resolved, validators independently fetch the live page and grade the answer: a validator agrees only when its own reading reaches the same outcome, the leader's quote is found word for word in the validator's own copy of the page, and the two answers state the same fact.

## Live app

https://pagewitness.vercel.app

## Contract

- Network: GenLayer Studionet (chain 61999)
- Contract address: 0xBBE090C5c5cCd8a93A899867DE41a5c13a8f628D
- Explorer: https://explorer-studio.genlayer.com/address/0xBBE090C5c5cCd8a93A899867DE41a5c13a8f628D
- Contract source, tests, and documentation: https://github.com/0xsters/genlayer-pagewitness

## What the app does

- Reads the live question count and every stored question, answer, and quote directly from the contract (genlayer-js, Studionet).
- Connects a browser wallet, adding the GenLayer Studionet network when missing.
- Registers questions with the contract's `ask` method.
- Resolves questions with `answer_query`, which triggers validator reading of the page, and waits for finalization before refreshing the answer.

## Run it

This is a single static page. Serve `index.html` from any static host, or open the live app above. No build step and no backend: all reads and writes go straight to the GenLayer Studionet RPC through genlayer-js loaded from a CDN.

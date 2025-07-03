# Quote Craft

```md
Project Structure
│
└─── Part 1 : BTCUSDT (Bitcoin derivative contract against Tether)
│   │   
│   └─── Started with a Naive Market Making Strategy, as a benchmark.
│   └─── Compared it with our Inventory Aware Market Making Strategy.
│   └─── Implemented realistic slippage and execution.
│   └─── Tested our strategy on three consecutive days. 
│
└─── Part 2 : (Future Improvement)
│   │   
│   └─── Paper Trading using Alpaca API
```

## Part 1

This part of the project aims to implement an intelligent market-making strategy, generating calculated quotes on order book data. It is structured as Python notebooks designed to simulate quoting, execution, and inventory management in a high-frequency trading environment. The simulator aims to help understand and evaluate simple market-making behaviors under realistic market conditions.

- **`Market_Making_final.ipynb`**  
  Contains the **base version** of the simulator. Quotes are placed deterministically at spread-adjusted prices, and fills are assumed to happen immediately when a price match occurs. Useful for understanding core logic: quoting, execution, inventory management, and mark-to-market PnL tracking.

- **Naive Market Neutral Strategy** (benchmark)

> - !["Strat 1"](1-10June2025_strat0.png)
> - (Performance = 68 %)

- **Inventory Aware Smart Strategy**

> - !["Strat 1"](1-10June2025_strat1.png)
> - (Performance = 79 %)

This strategy saves us from the risk due to holding a big position.

- **`Realistic.ipynb`**  
  Extends the base simulator with two realism enhancements:
  - **Execution Probability:** Not all limit orders are assumed to be filled. Each order has a probabilistic chance of execution, simulating queue position and competition.
  - **Gaussian Slippage:** When trades are executed, the price is adjusted with a small random noise to reflect market slippage and non-instant execution.
  
As expected, this leads to more volatile PnL outcomes, and emphasizes the risk of non-execution and price impact. 

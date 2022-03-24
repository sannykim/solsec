# Solana Auditing and Security Resources

A collection of resources to study Solana smart contract security, auditing, and exploits.



## Foundations 📚

- [Armani Sealevel Attacks and How to avoid them in Anchor](https://github.com/project-serum/sealevel-attacks)
  - [Summary Thread](https://twitter.com/pencilflip/status/1483880018858201090) by pencilflip
- [Armani Tips on Developing Secure Solana Programs](https://twitter.com/armaniferrante/status/1411589629384355840)
- [CMichel How to become a smart contract auditor](https://cmichel.io/how-to-become-a-smart-contract-auditor/) 
  - Targeted at ETH folks but contains general advice
- [DeFi MOOC samczsun Practical Smart Contract Security](https://www.youtube.com/watch?v=pJKy5HWuFK8)
  - Great intro to smart contract security that provides an overview of a large surface area of attacks. Mostly ETH-based but also covers a cross-chain BTC/ETH exploit and contains lots of concepts that carry over to Solana
- [Kudelski Solana Program Security](https://research.kudelskisecurity.com/2021/09/15/solana-program-security-part1/)
- [Neodyme Common Pitfalls](https://blog.neodyme.io/posts/solana_common_pitfalls)
- [Neodyme Solana Security Workshop Exercises and Solutions](https://workshop.neodyme.io/)
- [Neodyme Thinking Like An Attacker Workshop Recording](https://www.youtube.com/watch?v=vbkhhgeP30I)
- [OtterSec Solana from an Auditor’s perspective](https://osec.io/blog/tutorials/2022-03-14-solana-security-intro/)
- [Soteria Arithmetic Overflow and Underflow](https://www.soteria.dev/post/understanding-arithmetic-overflow-underflows-in-rust-and-solana-smart-contracts)
- [Soteria How to Audit Part 1: A Systematic Approach](https://www.soteria.dev/post/how-to-audit-solana-smart-contracts-part-1-a-systematic-approach)
- [Soteria How to Audit Part 2: using automated tools to find vulnerabilities](https://www.soteria.dev/post/how-to-audit-solana-smart-contracts-part-2-automated-scanning)
- [Soteria How to Audit Part 3: Penetration Testing](https://www.soteria.dev/post/how-to-audit-solana-smart-contracts-part-3-penetration-testing)
- [Soteria How to Audit Part 4: Anchor](https://www.soteria.dev/post/how-to-audit-solana-smart-contracts-part-4-the-anchor-framework)
- [Soteria Owner and Signer Check](https://www.soteria.dev/post/from-ethereum-smart-contracts-to-solana-programs-two-common-security-pitfalls-and-beyond)
- [Solend Auditing Workshop](https://docs.google.com/presentation/d/1jZ9kVo6hnhBsz3D2sywqpMojqLE5VTZtaXna7OHL1Uk/edit?pli=1#slide=id.ge15c343642_0_51) 
  - Known attacks from ETH and how they carry over to Solana + auditing methodology
- [Trail of Bits DeFi Security Success Stories](https://www.youtube.com/watch?v=jGrtK5k0CK0)
  - ETH-focused but broadly applicable advice on securing systems in DeFi


## Exploits 🪦

- [CASH Hack summary thread](https://twitter.com/samczsun/status/1506578902331768832) (samczsun)
- [Cope Roulette](https://github.com/Arrowana/cope-roulette-pro) (Arrowana)
- [Detecting Simulation in a Solana Program](https://opcodes.fr/en/publications/2022-01/detecting-transaction-simulation/) (Opcodes)
  - Goes into how transaction simulation works and the purpose of the bank - Soteria also has a great [overview](https://www.soteria.dev/post/solana-internals-part-4-the-bank-a-key-component) of the bank module
- [How to freely borrow all the TVL from the Jet Protocol](https://medium.com/@0xjayne/how-to-freely-borrow-all-the-tvl-from-the-jet-protocol-25d40e35920e) (Jayne)
- [How to Become a Millionaire, 0.000001 BTC at a Time](https://blog.neodyme.io/posts/lending_disclosure) (Neodyme)
  - [Context on Neodyme Exploit by Solend](https://blog.solend.fi/bug-bounty-and-response-to-spl-lending-vulnerability-f4c8874342d0)
- [New Integer Overflow Bug Discovered in Solana rBPF](https://blocksecteam.medium.com/new-integer-overflow-bug-discovered-in-solana-rbpf-7729717159ee) (BlockSec)
  - Use `checked_add(), checked_div(), checked_mul(), checked_pow, checked_sub` or `saturating_add(), saturating_mul(), saturating_pow(), saturating_sub()` → read relevant [Soteria blog post](https://www.soteria.dev/post/understanding-arithmetic-overflow-underflows-in-rust-and-solana-smart-contracts)
- [Schrodinger’s NFT, An Incinerator SPL Token program, and The Royal Flush Attack](https://medium.com/@solens_io/schrodingers-nft-an-incinerator-spl-token-program-and-the-royal-flush-attack-58e4ce4e63dc) (Solens) (similar to samczsun explanation of combining attacks)
- [Smashing the Candy Machine for fun and profit!](https://medium.com/@solens_io/smashing-the-candy-machine-for-fun-and-profit-a3bcc58d6c30) (Solens)
  - Check unchecked accounts properly! There is a reason why Anchor [requires](https://github.com/project-serum/anchor/pull/1452#discussion_r809207430) `UncheckedAccount` to have `/// CHECK` documentation. The fix came down to 1 line of Anchor code: `#[account(zero)]` vs `#[account(zero)]`
- [Solana Stake Pool: A Semantic Inconsistency Vulnerability](https://www.soteria.dev/post/solana-stake-pool-a-semantic-inconsistency-vulnerability-discovered-by-soteria) (Soteria)
  - Shows how to build a proof of concept with Neodyme’s Poc Framework. Also highlights how previously audited code (Stake Pool audits linked in audits section below) can contain vulnerabilities
- [SPL Token Program Approve Instruction](https://2501babe.github.io/tools/revoken.html) (Hana)
- [The $200m Bluff: Cheating Oracles on Solana](https://osec.io/blog/reports/2022-02-16-lp-token-oracle-manipulation/) (OtterSec)
- [Wormhole Hack TLDR](https://halborn.com/explained-the-wormhole-hack-february-2022/) (Halborn)
- [Wormhole Hack Quick Analysis](https://research.kudelskisecurity.com/2022/02/03/quick-analysis-of-the-wormhole-attack/) (Kudelski)
- [Wormhole Post-Mortem Analysis](https://extropy-io.medium.com/solanas-wormhole-hack-post-mortem-analysis-3b68b9e88e13) (Entropy)
- [Wormhole Hack Lessons](https://blog.chainalysis.com/reports/wormhole-hack-february-2022/) (Chainanalysis)



## Tools 🔧

- [Neodyme Solana PoC Framework](https://github.com/neodyme-labs/solana-poc-framework) (penetration testing)
- [Saber Vipers](https://github.com/saber-hq/vipers) (checks and validations)
- [Kudelski Semgrep](https://twitter.com/cryptographadam/status/1425163382982811650?s=20&t=5rNeZ11MMw0N1e-_SmU5Tw) (static analysis)
- [Soteria](https://www.soteria.dev/post/soteria-a-vulnerability-scanner-for-solana-smart-contracts) (vulnerability scanner)



## Bug Bounties **🏆**

- [Drift](https://immunefi.com/bounty/driftprotocol/) (up to 500k)
- [Jet](https://immunefi.com/bounty/jetprotocol/) (up to 75k)
- [Larix](https://docs.projectlarix.com/how-to-prove/bug-bounty-reward) (up to 150k)
- [Lido](https://immunefi.com/bounty/lidoforsolana/) (up to 2m)
- [Mango](https://docs.mango.markets/mango/bug-bounty) (up to 1m)
- [Marinade](https://immunefi.com/bounty/marinade/) (up to 250k)
- [Port](https://immunefi.com/bounty/portfinance/) (up to 500k)
- [Solana Labs](https://github.com/solana-labs/solana/security/policy) (up to 2m)
- [Solend](https://docs.solend.fi/protocol/bug-bounty) (up to 1m)
- [UXD](https://docs.uxd.fi/uxdprotocol/resources/bug-bounty) (up to 2.5m)
- [Wormhole](https://immunefi.com/bounty/wormhole/) (up to 10m)



## Audits and Code Reviews 🔒

- [Aldrin](https://dex.aldrin.com/877f900320eec44c13409814fe473fb7.pdf) (Kudelski)
- [Cropper](https://github.com/HalbornSecurity/PublicReports/blob/master/Solana%20Program%20Audit/Cropper_Finance_AMM_Program_Security_Audit_Report_Halborn_Final.pdf) (Halborn)
- [GooseFx](https://github.com/HalbornSecurity/PublicReports/blob/master/Solana%20Program%20Audit/GooseFX_Swap_Program_Security_Audit_Report_Halborn_Final.pdf) (Halborn)
- [Larix](https://docs.projectlarix.com/how-to-prove/audit) (SlowMist)
- [Marinade](https://docs.marinade.finance/marinade-protocol/security/audits) (Kudelski + Ackee) and [Code Review](https://marinade.finance/docs/Neodyme.pdf) (Neodyme)
- [Parrot (Halborn)](https://doc.parrot.fi/Party_Parrot_Solana_Smart_Contract_Security_Audit_Report_Halborn_v1_1.pdf)
- [Phantasia](https://github.com/HalbornSecurity/PublicReports/blob/master/Solana%20Program%20Audit/Phantasia_Sports_NFT_Store_SPA_Solana_Program_Security_Audit_Report_Halborn_Final.pdf) (Halborn)
- [Quarry](https://github.com/QuarryProtocol/quarry/blob/master/audit/quantstamp.pdf) (Quantstamp)
- [Saber](https://github.com/saber-hq/stable-swap/blob/master/audit/bramah-systems.pdf) (Bramah Systems)
- [Shared Memory and Token Swap Code Review](https://orca-dev-12345.s3-ap-southeast-1.amazonaws.com/Kudelski-audit.pdf) (Kudelski)
- [Soda](https://certik-public-assets.s3.amazonaws.com/REP-Soda-Protocol-2021-10-26.pdf) (Certik)
- [Solana](https://solana.com/solana-security-audit-2019.pdf) (Kudelski) (2019)
- [Solana Stake Pool](https://solana.com/SolanaKudelskiStakePoolAudit.pdf) (Kudelski)
- [Solana Stake Pool](https://solana.com/SolanaQuantstampStakePoolAudit.pdf) (Quantstamp)
- [Solend](https://docs.solend.fi/protocol/audit) (Kudelski)
- [Streamflow](https://github.com/streamflow-finance/rust-sdk/blob/main/protocol_audit.pdf) (Opcodes)
- [UXD Audit](https://docs.uxd.fi/uxdprotocol/resources/audits) (Bramah Systems)
- [Wormhole](https://github.com/certusone/wormhole/blob/dev.v2/audits/2021-01-10_neodyme.pdf) (Neodyme)



## Open Questions ？

- [When is it appropriate to reward a bounty?](https://twitter.com/wireless_anon/status/1501025792565915657)
- [When to audit a protocol?](https://twitter.com/ChenWainuo/status/1499871348696379393), [thread on deploying to mainnet without an audit](https://twitter.com/cronos_so/status/1500131620606681088)
- [Who would pay for an Anchor exploit?](https://twitter.com/armaniferrante/status/1506691213394694152)



## Contributing 🤝

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.


## License 🪧

Feel free to do whatever you want with this material (but pls be a whitehacker)!

# Solana Auditing and Security Resources

A collection of resources to study Solana smart contract security, auditing, and exploits.



## Foundations 📚

- [Armani Sealevel Attacks and How to avoid them in Anchor](https://github.com/project-serum/sealevel-attacks)
  - [Summary Thread](https://twitter.com/pencilflip/status/1483880018858201090) by pencilflip - use Anchor attributes, constraints and types, it will make your life easier!
- [Armani Tips on Developing Secure Solana Programs](https://twitter.com/armaniferrante/status/1411589629384355840)
  - Be wary of  `UncheckedAccount` and `AccountInfo` - check them properly!
- [CMichel How to become a smart contract auditor](https://cmichel.io/how-to-become-a-smart-contract-auditor/) 
  - Targeted at ETH folks but contains general advice
- [DeFi MOOC samczsun Practical Smart Contract Security](https://www.youtube.com/watch?v=pJKy5HWuFK8)
  - Great intro to smart contract security that provides an overview of a large surface area of attacks. Mostly ETH-based but also covers a cross-chain BTC/ETH exploit, and contains lots of concepts that carry over to Solana
- [Kudelski Solana Program Security](https://research.kudelskisecurity.com/2021/09/15/solana-program-security-part1/)
  - A high-level overview of ownership and data validation
- [Neodyme Common Pitfalls](https://blog.neodyme.io/posts/solana_common_pitfalls)
  - Check owner, check signer, check account data, be careful of integer over/underflow, verify invoke_signed(), and [use Anchor](https://twitter.com/armaniferrante/status/1438706351295827968?s=20&t=YS6ldLG-nvqLffT4eZtpKg) (unless you have a good reason not to), e.g. account confusions are prevented in Anchor by implicitly assigning each `#[account]` a type with an 8-byte identifier 
- [Neodyme Solana Security Workshop Exercises and Solutions](https://workshop.neodyme.io/)
  - Corresponding exercises to the common pitfalls mentioned in the blog post 
- [Neodyme Thinking Like An Attacker Workshop Recording](https://www.youtube.com/watch?v=vbkhhgeP30I)
  - A quick rundown of the PoC framework and an explanation of Level 0 of the challenge
- [OtterSec Solana from an Auditor’s perspective](https://osec.io/blog/tutorials/2022-03-14-solana-security-intro/)
  - A bottoms-up introduction to Solana's Execution and Programming Model from a security perspective
- [Sec3 Arithmetic Overflow and Underflow](https://www.sec3.dev/blog/understanding-arithmetic-overflow-underflows-in-rust-and-solana-smart-contracts)
  - Don't use `+, - , /, *` operations, check arithmetic operations for overflow and underflow!
- [Sec3 How to Audit Part 1: A Systematic Approach](https://www.sec3.dev/blog/how-to-audit-solana-smart-contracts-part-1-a-systematic-approach)
  - A high-level overview of common attack surfaces and questions to ask as an auditor
- [Sec3 How to Audit Part 2: using automated tools to find vulnerabilities](https://www.sec3.dev/blog/how-to-audit-solana-smart-contracts-part-2-automated-scanning)
  - An outline of tools that can automatically scan your code for vulnerabilities, unsafe Rust, and spelling. More security tools are needed! 
- [Sec3 How to Audit Part 3: Penetration Testing](https://www.sec3.dev/blog/how-to-audit-solana-smart-contracts-part-3-penetration-testing)
  - How to execute a proof of concept for an attack with Neodyme's PoC framework
- [Sec3 How to Audit Part 4: Anchor](https://www.sec3.dev/blog/how-to-audit-solana-smart-contracts-part-4-the-anchor-framework)
  - How Anchor's `#[program] `, `#[derive(Accounts)]` and `#[account]`work under-the-hood
- [Sec3 Owner and Signer Check](https://www.sec3.dev/blog/from-ethereum-smart-contracts-to-solana-programs-two-common-security-pitfalls-and-beyond)
  - Check the owner and check the signer! Use `#[account]` and `Signer<'info>` to [prevent](https://twitter.com/armaniferrante/status/1438706352805797889?s=20&t=YS6ldLG-nvqLffT4eZtpKg) this
- [Solend Auditing Workshop](https://docs.google.com/presentation/d/1jZ9kVo6hnhBsz3D2sywqpMojqLE5VTZtaXna7OHL1Uk/edit?pli=1#slide=id.ge15c343642_0_51) 
  - Known attacks from ETH and how they carry over to Solana + auditing methodology
- [Trail of Bits DeFi Security Success Stories](https://www.youtube.com/watch?v=jGrtK5k0CK0)
  - ETH-focused but broadly applicable advice on securing systems in DeFi
- [Zellic The Vulnerabilities You’ll Write With Anchor](https://www.zellic.io/blog/the-vulnerabilities-youll-write-with-anchor/)
  - A subset of common vulnerabilities you'll come across in Anchor programs



## Exploits 🪦

- [CASH Hack Summary Thread](https://twitter.com/samczsun/status/1506578902331768832) (samczsun)
  - Establish a root of trust!
- [CASH Hack — What’s the Vulnerability](https://www.sec3.dev/blog/cashioapp-attack-whats-the-vulnerability-and-how-soteria-detects-it) (Sec3)
  - Check input accounts!
- [Cope Roulette](https://github.com/Arrowana/cope-roulette-pro) (Arrowana)
  - Neat way to exploit reverting transactions
- [Detecting Simulation in a Solana Program](https://opcodes.fr/en/publications/2022-01/detecting-transaction-simulation/) (Opcodes)
  - Goes into how transaction simulation works and the purpose of the bank - Sec3 also has a great [overview](https://www.sec3.dev/blog/solana-internals-part-4-the-bank-a-key-component) of the bank module
- [How to freely borrow all the TVL from the Jet Protocol](https://medium.com/@0xjayne/how-to-freely-borrow-all-the-tvl-from-the-jet-protocol-25d40e35920e) (Jayne)
  - A fairly uncommon vulerability due to an unintended use of `break`
- [How to Become a Millionaire, 0.000001 BTC at a Time](https://blog.neodyme.io/posts/lending_disclosure) (Neodyme)
  - An innocent-looking rounding error that put $2.6bn at risk. If in doubt, use `floor` (or `ceil` depending on direction) instead of `round`
  - [Context on Neodyme Exploit by Solend](https://blog.solend.fi/bug-bounty-and-response-to-spl-lending-vulnerability-f4c8874342d0)
- [New Integer Overflow Bug Discovered in Solana rBPF](https://blocksecteam.medium.com/new-integer-overflow-bug-discovered-in-solana-rbpf-7729717159ee) (BlockSec)
  - Use `checked_add(), checked_div(), checked_mul(), checked_pow, checked_sub` or `saturating_add(), saturating_mul(), saturating_pow(), saturating_sub()`! → read relevant [Sec3 blog post](https://www.sec3.dev/blog/understanding-arithmetic-overflow-underflows-in-rust-and-solana-smart-contracts)
- [Schrodinger’s NFT, An Incinerator SPL Token program, and The Royal Flush Attack](https://medium.com/@solens_io/schrodingers-nft-an-incinerator-spl-token-program-and-the-royal-flush-attack-58e4ce4e63dc) (Solens) (similar to samczsun explanation of combining attacks)
  - Chaining small exploits to create a significant exploit. Watch [samczsun's explanation](https://www.youtube.com/watch?v=oA6Td5ujGrM) of exploit chaining 
- [Smashing the Candy Machine for fun and profit!](https://medium.com/@solens_io/smashing-the-candy-machine-for-fun-and-profit-a3bcc58d6c30) (Solens)
  - Check unchecked accounts properly! There is a reason why Anchor [requires](https://github.com/project-serum/anchor/pull/1452#discussion_r809207430) `UncheckedAccount` to have `/// CHECK` documentation. The fix came down to 1 line of Anchor code: `#[account(zero)]` vs `#[account(zero)]`
- [Solana Stake Pool: A Semantic Inconsistency Vulnerability](https://www.sec3.dev/blog/solana-stake-pool-a-semantic-inconsistency-vulnerability-discovered-by-soteria) (Sec3)
  - Shows how to build a proof of concept with Neodyme’s Poc Framework. Also highlights how previously audited code (Stake Pool audits linked in audits section below) can contain vulnerabilities
- [Solend Malicious Lending Market Incident Report](https://docs.google.com/document/d/1-WoQwT1QrPEX-r4N-fDamRQ50LM8DsdsOyq1iTabS3Q/edit#)  (Rooter)
  - Read Kudelski's blog post on Solana Program Security to understand the exploit
- [SPL Token Program Approve Instruction](https://2501babe.github.io/tools/revoken.html) (Hana)
  - Sneaky way to revoke Solana token approvals
- [The $200m Bluff: Cheating Oracles on Solana](https://osec.io/blog/reports/2022-02-16-lp-token-oracle-manipulation/) (OtterSec)
  - How to move an AMM price to manipulate an oracle and exploit a lending protocol. Use fair pricing for LP tokens and TWAPs where possible! Drift has [examples of oracle guardrails](https://github.com/drift-labs/protocol-v1/blob/4c2d447a677693da506e4de9596a07e4b9ba4d5d/tests/admin.ts#L212) that aim to prevent these types of attacks
- [Wormhole Hack Summary Thread](https://twitter.com/samczsun/status/1489044939732406275) (samczsun)
  - Check/validate your input accounts anon!
- [Wormhole Hack TLDR](https://halborn.com/explained-the-wormhole-hack-february-2022/) (Halborn)
  - When chaining delegations of signature verifications, make sure it leads to proper verifications!
- [Wormhole Hack Quick Analysis](https://research.kudelskisecurity.com/2022/02/03/quick-analysis-of-the-wormhole-attack/) (Kudelski)
  - Validate [unmodified, reference-only accounts](https://docs.solana.com/developing/programming-model/accounts#verifying-validity-of-unmodified-reference-only-accounts)!
- [Wormhole Post-Mortem Analysis](https://extropy-io.medium.com/solanas-wormhole-hack-post-mortem-analysis-3b68b9e88e13) (Entropy)
  - Analyzing the input accounts to fake the `SignatureSet`



## PoCs for Discovered Vulnerabilities 💡

- [Cashio Exploit](https://github.com/PwnedNoMore/cashio-exploit-workshop/tree/poc) (PNM)
- [Jet Governance](https://github.com/otter-sec/jet-governance-pocs) (OtterSec)
- [Port Max Withdraw Bug](https://github.com/port-finance/variable-rate-lending/blob/master/token-lending/program/tests/max_withdraw_bug_poc.rs) (nojob)
- [SPL Token-Lending](https://blog.neodyme.io/posts/lending_disclosure) (Neodyme)



## Audits and Code Reviews 🔒

- [Aldrin](https://dex.aldrin.com/877f900320eec44c13409814fe473fb7.pdf) (Kudelski)
- [Audius](https://assets.website-files.com/6024b69839b1b755528798ea/6201872afb297b3955e303aa_Audius%20-%20Security%20Assessment%20for%20Audius%20Protocol%20v1.1.0.pdf) (Kudelski)
- [Cashmere](https://github.com/cashmere-inc/multisig-audit-report/blob/main/cashmere-audit-public.pdf) (OtterSec)
- [Cega](https://github.com/otter-sec/cega-vault-report) (OtterSec)
- [Crema](https://www.bramah.systems/audits/Crema_Finance_Audit_Bramah.pdf) (Bramah)
- [Cropper](https://github.com/HalbornSecurity/PublicReports/blob/master/Solana%20Program%20Audit/Cropper_Finance_AMM_Program_Security_Audit_Report_Halborn_Final.pdf) (Halborn)
- [Debridge](https://docs.debridge.finance/the-core-protocol/security#has-debridge-been-audited) (Neodyme)
- [Drift](https://github.com/Zellic/publications/blob/master/Drift%20Protocol%20Audit%20Report.pdf) (Zellic)
- [Francium](https://www.certik.com/projects/francium) (Certik)
- [Friktion](https://docs.friktion.fi/protocol/security) (Kudelski)
- [Genopets](https://whitepaper.genopets.me/tokenomics/gene-staking/staking-program-audit) (MadShield)
- [GooseFx](https://github.com/HalbornSecurity/PublicReports/blob/master/Solana%20Program%20Audit/GooseFX_Swap_Program_Security_Audit_Report_Halborn_Final.pdf) (Halborn)
- [Hedge](https://docs.hedge.so/protocol-overview/security) (Kudelski, OtterSec + Sec3)
- [Hubble](https://docs.hubbleprotocol.io/documentation/security-audits) (Kudelski)
- [Invariant](https://invariant.app/audit.pdf) (Sec3)
- [Jet Governance](https://github.com/jet-lab/jet-governance/blob/master/reports/jet-governance-audit-public.pdf) (OtterSec)
- [Juiced](https://juiced.fi/audit-report.pdf) (OtterSec)
- [Larix](https://docs.projectlarix.com/how-to-prove/audit) (SlowMist)
- [Light](https://github.com/Lightprotocol/light-protocol-program/blob/main/Audit/Light%20Protocol%20Audit%20Report.pdf) (HashCloak)
- [Mango](https://docs.mango.markets/audit) (Neodyme)
- [Maple](https://uploads-ssl.webflow.com/6247b0423c35b87bbaaf6d4c/62617902491def721f481ecb_Maple_Finance_Audit_Bramah.pdf) (Bramah)
- [Marinade](https://docs.marinade.finance/marinade-protocol/security/audits) (Kudelski + Ackee) and [Code Review](https://marinade.finance/docs/Neodyme.pdf) (Neodyme)
- [Marinade v2](https://github.com/marinade-finance/liquid-staking-program) (Neodyme + Sec3)
- [Mean](https://docs.meanfi.com/products/safety-and-security) (Sec3)
- [Orca Whirlpools](https://docs.orca.so/#has-orca-been-audited) (Kudelski + Neodyme)
- [Parrot](https://doc.parrot.fi/Party_Parrot_Solana_Smart_Contract_Security_Audit_Report_Halborn_v1_1.pdf) (Halborn)
- [Phantasia](https://github.com/HalbornSecurity/PublicReports/blob/master/Solana%20Program%20Audit/Phantasia_Sports_NFT_Store_SPA_Solana_Program_Security_Audit_Report_Halborn_Final.pdf) (Halborn)
- [Phoenix](https://github.com/Ellipsis-Labs/phoenix-v1/tree/master/audits) (MadShield + OtterSec)
- [Port Lending](https://immunefi.com/bounty/portfinance/) (Kudelski + SlowMist)
- [Port Sundial](https://github.com/port-finance/sundial/blob/master/audits/port-finance-sundial-audit-public.pdf) (OtterSec)
- [Pyth](https://github.com/Zellic/publications) (Zellic)
- [Quarry](https://github.com/QuarryProtocol/quarry/blob/master/audit/quantstamp.pdf) (Quantstamp)
- [Saber](https://github.com/saber-hq/stable-swap/blob/master/audit/bramah-systems.pdf) (Bramah)
- [Shared Memory and Token Swap Code Review](https://orca-dev-12345.s3-ap-southeast-1.amazonaws.com/Kudelski-audit.pdf) (Kudelski)
- [Soda](https://certik-public-assets.s3.amazonaws.com/REP-Soda-Protocol-2021-10-26.pdf) (Certik)
- [Solana](https://solana.com/solana-security-audit-2019.pdf) (Kudelski, 2019)
- [Solana Stake Pool](https://solana.com/SolanaKudelskiStakePoolAudit.pdf) (Kudelski)
- [Solana Stake Pool](https://solana.com/SolanaNeodymeStakePoolAudit.pdf) (Neodyme)
- [Solana Stake Pool](https://solana.com/SolanaQuantstampStakePoolAudit.pdf) (Quantstamp)
- [Solend](https://docs.solend.fi/protocol/audit) (Kudelski)
- [Solido](https://github.com/ChorusOne/solido/tree/163b26aee08958fbdc0f3909ccb6ef606a1ea0f2/audit) (Bramah + Neodyme)
- [Solvent](https://drive.google.com/file/d/1tVe-0EQhslQxr56nOQmxqaB8BSDwJ1s1/view) (OtterSec)
- [Squads](https://github.com/Squads-Protocol/squads-mpl/blob/main/Squads%20V3%20-%20OtterSec%20Audit.pdf) (OtterSec)
- [Streamflow](https://github.com/streamflow-finance/rust-sdk/blob/main/protocol_audit.pdf) (Opcodes)
- [Swim](https://swim.io/audits/kudelski.pdf) (Kudelski)
- [Synthetify](https://synthetify.io/resources/audit.pdf) (Kudelski)
- [UXD Audit](https://docs.uxd.fi/uxdprotocol/resources/audits) (Sec3)
- [Wormhole](https://github.com/certusone/wormhole/blob/dev.v2/audits/2021-01-10_neodyme.pdf) (Neodyme)



## Tools 🔧

- [Ackee Trdelnik](https://github.com/Ackee-Blockchain/trdelnik) (Anchor testing framework)
- [Anchor Test UI](https://github.com/0xPratik/anchor-UI) (Visual Anchor testing framework)
- [APR](https://www.apr.dev/) (Anchor Program Registry)
- [Blockworks Checked Math](https://github.com/blockworks-foundation/checked-math) (Macro to check math operations)
- [cargo-audit](https://docs.rs/cargo-audit/latest/cargo_audit) (checks Cargo.lock files for vulnerable crates)
- [cargo-geiger](https://crates.io/crates/cargo-geiger) (checks usage of unsafe Rust code)
- [Kudelski Semgrep](https://twitter.com/cryptographadam/status/1425163382982811650?s=20&t=5rNeZ11MMw0N1e-_SmU5Tw) (static analysis)
- [Neodyme Solana PoC Framework](https://github.com/neodyme-labs/solana-poc-framework) (penetration testing)
- [OtterSec Solana CTF Framework](https://github.com/otter-sec/sol-ctf-framework)
- [Saber Vipers](https://github.com/saber-hq/vipers) (checks and validations)
- [Sec3 Auto Auditor](https://twitter.com/aeyakovenko/status/1529138221094883333) (vulnerability scanner)
- [L3X](https://github.com/VulnPlanet/l3x) - (AI-driven Smart Contract Static Analyzer)



## Bug Bounties **🏆**

- [Drift](https://immunefi.com/bounty/driftprotocol/) (up to 500k)
- [Friktion](https://docs.friktion.fi/protocol/security) (up to 100k)
- [Hubble](https://github.com/hubbleprotocol/audits/blob/master/docs/SECURITY.md) (up to 500k)
- [Jet](https://immunefi.com/bounty/jetprotocol/) (up to 75k)
- [Larix](https://docs.projectlarix.com/how-to-prove/bug-bounty-reward) (up to 150k)
- [Lido](https://immunefi.com/bounty/lidoforsolana/) (up to 2m)
- [Mango](https://docs.mango.markets/mango/bug-bounty) (up to 1m)
- [Marinade](https://immunefi.com/bounty/marinade/) (up to 250k)
- [Metaplex](https://www.metaplex.com/bounty-program) (up to 200k)
- [Orca](https://immunefi.com/bounty/orca/) (up to 500k)
- [Port](https://immunefi.com/bounty/portfinance/) (up to 500k)
- [Phoenix](https://github.com/Ellipsis-Labs/phoenix-v1/security) (up to 100k)
- [Saber](https://blog.saber.so/the-cashio-vulnerability-against-saber-and-our-users-what-happened-and-what-we-are-doing-about-it-d0ee188e8346) (up to 1m)
- [Serum](https://forum.projectserum.com/t/formalizing-a-bug-bounty-program/410) (up to 1m)
- [Solana Labs](https://github.com/solana-labs/solana/security/policy) (up to 2m)
- [Solend](https://docs.solend.fi/protocol/bug-bounty) (up to 1m)
- [Solvent](https://solvent-protocol.gitbook.io/solvent-protocol/developers/bug-bounty) (up to 250k)
- [Swim](https://immunefi.com/bounty/swimprotocol/) (up to 100k)
- [Synthetify](https://synthetify.io/blog/bug-bounty) (up to 100k)
- [UXD](https://docs.uxd.fi/uxdprotocol/resources/bug-bounty) (up to 2.5m)
- [Wormhole](https://immunefi.com/bounty/wormhole/) (up to 2.5m)



## Open Questions ？

- [When is it appropriate to reward a bounty?](https://twitter.com/wireless_anon/status/1501025792565915657)
- [When to audit a protocol?](https://twitter.com/ChenWainuo/status/1499871348696379393), [thread on deploying to mainnet without an audit](https://twitter.com/cronos_so/status/1500131620606681088)
- [Who would pay for an Anchor exploit?](https://twitter.com/armaniferrante/status/1506691213394694152)



## Contributing 🤝

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.


## License 🪧

Feel free to do whatever you want with this material (but pls be a whitehacker)!

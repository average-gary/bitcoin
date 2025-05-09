# Bitcoin CTV Payment Pool Hackathon Project Plan

## Project Overview
Building a prototype CLI tool that demonstrates how to use CTV (CheckTemplateVerify) payment pools for coinbase outputs to enable trustless distribution of mining rewards to up to 100 parties.

## Team
- 3 developers
- 8 hour timeframe
- Bitcoin & CTV expertise

## Technical Components

### 1. RPC Implementation & Pool Construction (4 hours)
- Implement new RPC endpoint for payment pool construction
- Integrate with existing CTV node implementation
- Define input parameters:
  - Number of participants (max 100)
  - Amount distribution
  - Fee rate (fixed at 1 sat/vbyte)
- Create merkle tree for participant outputs
- Generate CTV commitment structure
- Implement validation checks
- Test RPC functionality

### 2. Payout Mechanism (3 hours)
- Integrate Sapio Miniscript for spending logic
- Implement unrolling mechanism for up to 100 participants
- Create transaction templates
- Add signature verification
- Implement CLI interface for payout commands
- Handle fee calculations with 1 sat/vbyte assumption

### 3. Testing & Integration (1 hour)
- End-to-end testing with node
- Performance testing with various participant counts
- CLI usability testing
- Documentation

## Task Distribution

### Developer 1 (RPC & Pool Construction Lead)
- Lead RPC implementation
- CTV commitment structure
- Integration with node
- Documentation

### Developer 2 (Pool Logic & Testing)
- Implement merkle tree logic
- Validation checks
- Testing framework
- Integration testing

### Developer 3 (Payout & CLI)
- Sapio Miniscript integration
- CLI implementation
- Payout mechanism
- Transaction template creation

## Success Criteria
- Functional RPC endpoint for pool creation
- Working CLI interface
- Successful CTV commitment structure
- Working payout mechanism for up to 100 participants
- Demonstrated trustless distribution
- Test coverage for critical paths

## Technical Dependencies
- CTV-enabled Bitcoin node (existing in repo)
- Sapio Miniscript crate
- Bitcoin RPC framework

## Next Steps
1. Review and confirm task distribution
2. Set up development environment with CTV node
3. Begin parallel development tracks
4. Regular sync points (every 2 hours)
5. Integration testing
6. Final demo preparation

## Implementation Notes
- Fixed fee rate of 1 sat/vbyte for simplicity
- CLI-only interface
- Maximum support for 100 participants
- Using existing CTV node implementation in repo
- No additional security requirements beyond basic CTV guarantees

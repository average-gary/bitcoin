## Porting `sendmanycompacted` from C++ to Rust: Plan

This section documents the plan for rewriting the `sendmanycompacted` function from `rpcwallet.cpp` in Rust, using the [rust-bitcoin crate](https://docs.rs/bitcoin/latest/bitcoin/) and staying as close as possible to the original C++ implementation.

### Goals
- Faithfully port the logic and structure of the C++ function.
- Do **not** add or change dependencies without explicit approval.
- Use only the standard library and the `rust-bitcoin` crate.
- Stub/mock wallet and chain interactions as needed for now.

### Steps

1. **Function Signature and Types**
   - Define the Rust function signature, input, and output types.
   - Use Rust types (`HashMap`, `Option`, etc.) for parameters.
   - Decide if the function will use JSON (serde_json) or Rust structs for input/output.

2. **Parameter Parsing**
   - Parse the input map of addresses to amounts.
   - Parse optional parameters (radix, gas, node_fees, comment, etc.) with defaults.

3. **Wallet and Chain Abstractions**
   - Assume a `Wallet` struct with methods similar to the C++ version (e.g., `get_new_destination`, `get_balance`, `create_transaction`).
   - Stub/mock locking and chain state as needed.

4. **Sorting/Pairing Modes**
   - Implement output sorting logic (AS_IS, LEXICOGRAPHIC, PROBABILITY, etc.) using Rust iterators and sorting.

5. **Radix Tree Construction**
   - Build the transaction tree as in the C++ code, using Rust collections and types.
   - Handle the special logic for radix, gas, and node fees.

6. **Transaction Creation**
   - Use `rust-bitcoin` types (`Transaction`, `TxOut`, `Script`, etc.) to build transactions.
   - Use `bitcoin::hashes` for hashing and `bitcoin::blockdata::script` for scripts.

7. **Return Value**
   - Return a struct or JSON object with transaction hexes and metadata, as in the C++ code.

8. **Testing and Validation**
   - Ensure the Rust implementation matches the C++ logic and output.
   - Add tests or examples as appropriate.

### Design Considerations
- Stay as true to the original C++ implementation as possible.
- Only use new dependencies with explicit approval.
- Document any deviations or necessary Rust idioms in this README.

--- 
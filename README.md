# Solana Counter

This is a simple Solana program that manages a counter. It allows incrementing, decrementing, updating, and resetting the counter.

## Instructions

The program supports the following instructions:

1. **Increment**: Increases the counter by a specified value.
2. **Decrement**: Decreases the counter by a specified value. If the value is greater than the current counter value, the counter is set to 0.
3. **Update**: Sets the counter to a specified value.
4. **Reset**: Resets the counter to 0.

## Usage

To use this program, you can interact with it by creating transactions that include the appropriate instructions. The instructions are encoded as specified in the `CounterInstructions` enum.

### Instruction Encoding

- **Increment**: `0` followed by a little-endian encoding of the increment value (u32).
- **Decrement**: `1` followed by a little-endian encoding of the decrement value (u32).
- **Update**: `2` followed by a little-endian encoding of the new value (u32).
- **Reset**: `3` (no additional data).

## Example

Here is a simple example of how to interact with the Solana Counter Program using the provided test:

```rust
#[test]
fn test_counter() {
    // Setup accounts and program ID
    // ...

    // Increment
    let mut increment_instruction_data: Vec<u8> = vec![0];
    let increment_value = 40u32;
    increment_instruction_data.extend_from_slice(&increment_value.to_le_bytes());
    process_instruction(&program_id, &accounts, &increment_instruction_data).unwrap();
    assert_eq!(/* ... */);

    // Decrement
    let mut decrement_instruction_data: Vec<u8> = vec![1];
    let decrement_value = 20u32;
    decrement_instruction_data.extend_from_slice(&decrement_value.to_le_bytes());
    process_instruction(&program_id, &accounts, &decrement_instruction_data).unwrap();
    assert_eq!(/* ... */);

    // Update
    let mut update_instruction_data: Vec<u8> = vec![2];
    let update_value = 33u32;
    update_instruction_data.extend_from_slice(&update_value.to_le_bytes());
    process_instruction(&program_id, &accounts, &update_instruction_data).unwrap();
    assert_eq!(/* ... */);

    // Reset
    let reset_instruction_data: Vec<u8> = vec![3];
    process_instruction(&program_id, &accounts, &reset_instruction_data).unwrap();
    assert_eq!(/* ... */);
}

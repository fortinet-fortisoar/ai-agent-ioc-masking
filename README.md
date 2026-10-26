# Release Information

- **Version**: 1.0.1

- **Certified**: Yes

- **Publisher**: Fortinet

- **Scope**: Masking

- **Verified with Models**: NA

- [Release notes](./release_notes.md)

# IOC Masking Agent

Detects and masks IOCs, including emails, IP addresses, and file hashes, using pattern-matching regex rules before sending data to the LLM.

## Installation

This agent installs along with the FortiAI solution pack.

## Configuration

**Required MCP Servers**: NA

### Prerequisites

The following prerequisites must be met before using this agent:

- The FortiAI solution pack must be installed and configured with the Fortinet FortiAI connector.

  - To configure the FortiAI solution pack, refer to the [FortiAI](https://github.com/fortinet-fortisoar/solution-pack-fortinet-advisor/) solution pack documentation.
  - To configure the Fortinet FortiAI connector, refer to the [Fortinet FortiAI](https://docs.fortinet.com/fortisoar/connectors/fortinet-fortiai) connector documentation.

> [!Note]
> The FortiAI solution pack and the Fortinet FortiAI connector are preconfigured out-of-the-box with FortiSOAR `v8.0.1` and later.

## Input Parameters

The input must be provided as a JSON object.

| Parameter         | Description                                                                                                                                          |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| `data`            | Input data containing sensitive information to be masked or unmasked                                                                                 |
| `action`          | Operation type: `mask` to hide sensitive data or `unmask` to reveal masked data                                                                      |
| `detransform_map` | JSON object used to reconstruct original data when `action=unmask`. Optional within the same session, where the agent reuses the mappings stored during masking |

> [!Note]
> Mappings stored during masking are retained for the session for 24 hours by default.

## Response

The output is returned as a JSON object.

| Parameter         | Description                                                                                 |
|-------------------|---------------------------------------------------------------------------------------------|
| `data`            | Returned only when `action=unmask`; contains data after unmasking                           |
| `masked`          | Returned only when `action=mask`; contains only masked data                                 |
| `detransform_map` | JSON object containing mappings to reconstruct original data (present when `action=mask`)   |
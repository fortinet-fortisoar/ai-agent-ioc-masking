# Release Information

- **Version**: 1.0.0

- **Certified**: Yes

- **Publisher**: Fortinet

- **Scope**: Masking

- **Verified with Models**: NA

# IOC Masking Agent

Detects and masks IOC's including emails, IP addresses, filehash using pattern matching regex rules before sending data to the LLM.

## Installation

This agent installs along with the FortiAI solution pack.

## Configuration

**Required MCP Servers**: NA

<!-- > [!Note]
>
> Refer to [Configuring MCP Servers](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/823139/mcp-servers#Configure_MCP_Servers) on FortiSOAR platform documentation for information on configuring a custom MCP server.
>  -->

### Prerequisites

- The FortiAI solution pack must be installed and configured with the Fortinet FortiAI connector.

  - To configure the FortiAI solution pack, refer to the [FortiAI](https://github.com/fortinet-fortisoar/solution-pack-fortinet-advisor/) solution pack documentation.
  - To configure the Fortinet FortiAI connector, refer to the [Fortinet FortiAI](https://docs.fortinet.com/fortisoar/connectors/fortinet-fortiai) connector documentation.

> [!Note]
>
> FortiAI solution pack and Fortinet FortiAI connector are preconfigured out-of-the-box with FortiSOAR `v8.0.0`.
> 


## Input Parameters

The input must be provided as a JSON object.

| Parameter         | Description                                                                     |
|-------------------|---------------------------------------------------------------------------------|
| `data`            | Input data containing sensitive information to be masked or unmasked            |
| `action`          | Operation type: 'mask' to hide sensitive data or 'unmask' to reveal masked data |
| `detransform_map` | JSON object required when `action=unmask`; used to reconstruct original data    |


## Response

The output is returned as a JSON object.

| Parameter         | Description                                                                             |
|-------------------|-----------------------------------------------------------------------------------------|
| `data`            | Returned only when action=unmask; contains data after unmasking                         |
| `masked`          | Returned only when action=mask; contains only masked data                               |
| `detransform_map` | JSON object containing mappings to reconstruct original data (present when action=mask) |


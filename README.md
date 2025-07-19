# Companion Module for LightSync S2

A Bitfocus Companion module for controlling LightSync S2 devices via OSC (Open Sound Control) over UDP. This module provides comprehensive control over LightSync S2 functionality including cue management, remote control, port management, and sound presets.

## Features

- **Cue Control**: Advance and reverse cues with conditional USB port activation
- **Remote Management**: Toggle remote controls 1-4
- **Port Control**: Toggle USB ports 1-4
- **Sound Management**: Mute toggle and sound presets
- **IP Configuration**: Dynamic IP address configuration
- **Real-time Feedback**: Visual feedback for all device states
- **OSC Communication**: Full OSC protocol support over UDP

## Installation

### Method 1: Manual Installation

1. Clone or download this repository
2. Copy the `companion-module-lightsync-s2` folder to your Companion modules directory:
   - **Windows**: `%APPDATA%\companion\modules\`
   - **macOS**: `~/Library/Application Support/companion/modules/`
   - **Linux**: `~/.companion/modules/`
3. Restart Companion
4. Add a new instance of "LightSync S2" in Companion

### Method 2: Git Installation

```bash
cd ~/.companion/modules
git clone https://github.com/lightsync/companion-module-lightsync-s2.git
cd companion-module-lightsync-s2
npm install
```

## Configuration

### Connection Settings

| Setting | Description | Default |
|---------|-------------|---------|
| LightSync IP Address | IP address of your LightSync S2 device | 192.168.9.9 |
| Target Port | OSC communication port | 23532 |
| Protocol | Communication protocol | UDP |
| Feedback Port | Port for receiving feedback | 33533 |
| Enable Feedback Listening | Enable OSC feedback reception | Yes |

### Example Configuration

```
LightSync IP Address: 192.168.9.9
Target Port: 23532
Protocol: UDP
Feedback Port: 33533
Enable Feedback Listening: Yes
```

## Actions

### Cue Control
- **Advance All**: Advances all cues
- **Reverse All**: Reverses all cues
- **Advance if USB port is Active**: Advances only if USB port is active
- **Reverse if USB port is Active**: Reverses only if USB port is active

### Remote Control
- **Remote 1-4 Toggle**: Toggle individual remote controls

### Port Management
- **Port 1-4 Toggle**: Toggle individual USB ports

### Sound Control
- **Sound Mute Toggle**: Toggle sound mute state
- **Set Sounds**: Apply sound presets
  - **Preset 1**: Forward sound (3), Back sound (2)
  - **Preset 2**: Forward sound (5), Back sound (6)

### Configuration
- **Set Custom IP**: Configure Companion IP address for feedback
- **Set Feedback IP**: Configure feedback IP address

## Feedbacks

### Monitor Values
- **Monitor Value = 0 (Black)**: Triggered when monitor receives value 0
- **Monitor Value = 1 (Green)**: Triggered when green remote button is pressed
- **Monitor Value = 2 (Red)**: Triggered when red remote button is pressed

### Status Feedbacks
- **Mute Toggle**: Shows mute state (Green=Unmuted, Red=Muted)
- **Port 1-4 Toggle**: Shows port state (Green=On, Red=Off)
- **Remote 1-4 Toggle**: Shows remote state (Green=On, Red=Off)

## Variables

- **Button Press Count**: Tracks button press events
- **Monitor Value**: Current monitor feedback value

## OSC Protocol

This module communicates with LightSync S2 using OSC messages over UDP. Key OSC paths include:

### Outgoing Messages
- `/cue/i` - Cue control (1=advance, 2=reverse)
- `/cue/r` - Conditional cue control
- `/slot/toggle/1-4` - Remote control toggles
- `/port/1-4` - Port control toggles
- `/sound/mute` - Sound mute toggle
- `/sound/forward` - Forward sound setting
- `/sound/back` - Back sound setting
- `/custom/ip/1-4` - IP address configuration
- `/custom/ipOut/1-4` - Feedback IP configuration

### Incoming Messages
- `/companion/monitor/` - Monitor feedback values
- `/sound/mute` - Mute state feedback
- `/port/1-4` - Port state feedback
- `/slot/toggle/1-4` - Remote state feedback

## Development

### Prerequisites
- Node.js 16 or higher
- npm or yarn

### Setup
```bash
git clone https://github.com/lightsync/companion-module-lightsync-s2.git
cd companion-module-lightsync-s2
npm install
```

### Testing
```bash
npm test
```

## Troubleshooting

### Connection Issues
1. Verify the LightSync IP address and port settings
2. Check if your LightSync S2 device is powered on and connected to the network
3. Test connectivity using ping or telnet
4. Check firewall settings for UDP ports 23532 and 33533

### OSC Communication Issues
1. Verify OSC paths match your LightSync S2 configuration
2. Check that feedback listening is enabled if you need visual feedback
3. Ensure UDP ports are not blocked by firewall

### Feedback Not Working
1. Verify feedback port is correctly configured
2. Check that LightSync S2 is sending feedback to the correct IP
3. Ensure feedback listening is enabled in module configuration

## License

MIT License - see LICENSE file for details.

## Support

For support and issues, please visit:
- GitHub Issues: https://github.com/lightsync/companion-module-lightsync-s2/issues
- Documentation: https://github.com/lightsync/companion-module-lightsync-s2#readme 

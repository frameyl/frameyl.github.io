# Port Speed License

### Change List To Add Logs in Firmware Reading/Writing License File

1. CL#912310
2. CL#912798

### The Code Block to read/write Port Speed License

```Python
def loadSpeedLicense(self, params):
    logger.info('hyperd::loadSpeedLicense - New speed license received from BLL.  Loading license onto TM EEPROM...')
    board_type = self.server.board_obj.board_type.lower()
    subprocess.call(['/bin/eeprom_interface', '-b', board_type, '-i'])
    subprocess.call(['/bin/eeprom_interface', '-b', board_type, '-e'])
    subprocess.call(['/bin/eeprom_interface', '-b', board_type, '-w', '/mnt/spirent/hypervisor/conf/newspeedlicense.json'])
    self.sock.sendto('loadSpeedLicense: success', self.client_address)
```

```Python
def readSpeedLicense(self, params):
    logger.info('hyperd::readSpeedLicense - Reading speed license from TM EEPROM...')
    board_type = self.server.board_obj.board_type.lower()
    subprocess.call(['/bin/eeprom_interface', '-b', board_type, '-i'])
    subprocess.call(['/bin/eeprom_interface', '-b', board_type, '-r', '/mnt/spirent/hypervisor/conf/currentspeedlicense.json'])
    self.sock.sendto('readSpeedLicense: success', self.client_address)

```

### Location Of Port Speed License

On Nebula Appliance,

> /mnt/spirent/hypervisor/conf/currentspeedlicense.json

On Chassis,

> /mnt/spirent/testmodule/slot0/hypervisor/conf/currentspeedlicense.json

### To verify the read/write is working

1. Initialize

> #eeprom_interface -b nemesis -i 

2. Erase the eeprom

> \#eeprom_interface -b nemesis -e

3. Write from inputFile.json

>  \#eeprom_interface -b nemesis -w inputFile.json

4. Read back what is written, do the following:

> #eeprom_interface -b nemesis -r fileName.out

5. Make sure “inputFile.json” and “fileName.out” are the same

> \#diff inputFile.json fileName.out 
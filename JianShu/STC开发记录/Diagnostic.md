Problem does not seem to happen on all cards but on most cards it can be reproduced by:

Switch port speed to 25G
Reserve ports
Apply
Login to ccpu
Run /mnt/spirent/ccpu/bin/cttest/ct_tx_timestamp -i eth0 -c 2
Release ports
Reserve ports
Apply
Run /mnt/spirent/ccpu/bin/cttest/ct_tx_timestamp -i eth0 -c 1
Check /usr/spirent/log/logfile_bsdnetd.log for errors like:
09-28-18 23:07:39,240 [4135160640] INFO content.il.0.bsdnetd <> - eth0: got zero timestamp value, tail 0
09-28-18 11:33:36,358 [4134284096] INFO content.il.0.bsdnetd <> - eth0: failed to match timestamp seq_num, expected 0, got 232
Once tx timestamp queue is in a bad state it can easily be triggered by toggling the PLL reset bit


>root@slot1:/mnt/spirent/ccpu/bin/cttest# spamtool++ -a -p0 -r 0x80 -c 4
00000080: 00000000 00000000 00000000 00000000
root@slot1:/mnt/spirent/ccpu/bin/cttest# spamtool++ -a -p0 -w 0x204 0x10000
root@slot1:/mnt/spirent/ccpu/bin/cttest# spamtool++ -a -p0 -w 0x204 0x00000
root@slot1:/mnt/spirent/ccpu/bin/cttest# spamtool++ -a -p0 -r 0x80 -c 4
00000080: 00000000 00000000 00000008 00000000
root@slot1:/mnt/spirent/ccpu/bin/cttest# spamtool++ -a -p0 -r 0x80 -c 4
00000080: 00000000 00010000 00000006 00000000
root@slot1:/mnt/spirent/ccpu/bin/cttest# spamtool++ -a -p0 -r 0x80 -c 4
00000080: 00000000 00020000 00000004 00000000
root@slot1:/mnt/spirent/ccpu/bin/cttest# spamtool++ -a -p0 -r 0x80 -c 4
00000080: 00000000 00030000 00000002 00000000
root@slot1:/mnt/spirent/ccpu/bin/cttest# spamtool++ -a -p0 -r 0x80 -c 4
00000080: 00000000 00000000 00000000 00000000

BLL Log Features
================

1. ConnectToChassisCommand.2473(ConnectToChassisCommand 1) state: Started by; AddrList : smt-n11u-06-ms-01.calenglab.spirentcom.com
2. ReservePortCommand.2908(ReservePortCommand 1) state: Started by; Location : //smt-n11u-06-ms-01.calenglab.spirentcom.com/2/9 //smt-n11u-06-ms-01.calenglab.spirentcom.com/2/21
3. test module smt-n11u-06-ms-01.calenglab.spirentcom.com/2 marketing part number is PX3-100GQ-T12; test module smt-n11u-06-ms-01.calenglab.spirentcom.com/2 family is NEMESIS
4. Successfully reserved all ports
5. beta.pv.basic.ConfigPortAndSpeedAndANCommand.2917(PL Command: Configure Port And Speed And AN Command 1) state: Started; LineSpeed : SPEED_100G
6. ApplyToILCommand.2922(ApplyToILCommand 1) state: Completed took: 4.930 sec
7. Sequenser:
   7. SequencerStartCommand.4060(SequencerStartCommand 1) state: Completed took: 0.010 sec
   2. user.Sequencer       - Running command: Start Devices 1
   3. user.Sequencer       - Stop Capture 1 finished.  Elapsed time [00:00:00.502]
   4. SequencerStopCommand.3040(Stop Command Sequencer 12) state: Started in background by the user
   5. SequencerTestState : CHANGE_TO_FAILED
   6. StoppedReason : Stream failed to resolved state
   7. Sequencer finished.  Elapsed time [00:01:12.968]
8. Link Error:
   1. user.port            - ospfPort 2 //2/21: link status changed to Error (local fault).
   2. Link flap detected on port //hw-ci-n11u-01.calenglab.spirentcom.com/1/5 when traffic is running
9. IL Error:
   1. port //smt-11u-02.calenglab.spirentcom.com/12/3 event: Daemon analyzer_2093 died
   2. Rcvd error response: seq105 msgr port //10.109.116.12/1/1 req OSPFV2_1.GetReconfigurationState code 10000 faultMsg Daemon startup failed
   3. Not all command target objects reached their final state 0 successful, 1 unsuccessful
   4. Timed out waiting for EthCommonPHY_1.SetFlowControlConfig response after 600 seconds. Port connection will be lost.
   5. Wait for generator state to change from PENDING START to RUNNING timed out
10. Port Error
    1. smt-9u-02.calenglab.spirentcom.com test module 4 port group 3 did not become online/up after 1200 seconds.
    2. Failed to reserve 1 out of 1 ports
    3. 99% complete for smt-11u-02.calenglab.spirentcom.com test module 8 port group 7 to be up
11. Chassis Error:
    1. Failed to connect to chassis smt-dpdk-s2-02.calenglab.spirentcom.com.  Please check that equipment is online/up.
12. 
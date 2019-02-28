IutAutoCommand
  CreateInstanceCommand
  SourceIutAutoFileCommand
  CreateNameSpaceCommand
  EvalFileCommand
  EvalProcCommand

# Enable an automation scripts
AutomationHandler::CreateAutomationInstance(StcHandle handle)

# Sync IUT Configuration
AutomationHandler::SynchIutParams()

AutomationHandler::EvalUserScriptCmd

# Generate TCL code from XML
d:\Dev\p4\TestCenter\integration\content\cts\tsm\bll\automation\src\XmlAutomationHandler.cpp
std::string XmlAutomationHandler::GenerateAutomationCodeFromXml(std::string xmlFileName, bool genDebugCode)

# Call To Automation()
CCtsStartTestScenarioCommand::DoRun()
  CCtsRunSequenceCommand::DoRun()
    TestManagement::LoadTestSession(CTestProfile& tp)
      TestManagement::ApplyTestSessionData(CTestSession& session, CTestProfile& tp)
        CLoadSaveSessionProperties::LoadParameters(StcHandle sessionHandle, StcHandle testProfileHandle)
          CCtsLoadTestParamsCommand::DoRun()
            CCtsApplyTestParamsCommand::DoRun()
              session->GetAutomationHandler()->EnableAutomation();

  CCtsRunSequenceCommand::DoRun()
    CCtsRunSequenceCommand::StartSessionExecution(CTestSession& session)
      CCtsSynchIutConfigCommand::DoRun()
        AutomationHandler::SynchIutParams()

# CTS Automation Procedure
AutomationHandler::EnableAutomation()
  AutomationHandler::CreateAutomationInstance(StcHandle handle)
    new CreateInstanceCommand(m_ctsNamespace)
    AutomationHandler::InitAutoParameters(Automation* autoObj)
      new CreateNameSpaceCommand(autoObj, m_paramsNamespace)
      for testParams Sets:
        new CreateNameSpaceCommand(autoObj, propNamespace)
        autoObj->SetVar(m_paramsNamespace, propName, pval);
    XmlAutomationHandler::GenerateAutomationCodeFromXml(std::string xmlFileName, bool genDebugCode)
    new EvalFileCommand(autoObj, genFile)

AutomationHandler::SynchIutParams()
  new EvalProcCommand(autoObj, m_ctsNamespace, cmdName);


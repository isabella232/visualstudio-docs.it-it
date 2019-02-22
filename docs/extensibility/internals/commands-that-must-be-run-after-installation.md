---
title: I comandi che devono essere eseguiti dopo l'installazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d336e4a65178ff09f5db01dffeb5bedd3b5b946e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631393"
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandi che devono essere eseguiti dopo l'installazione
Se si distribuisce l'estensione tramite una *file con estensione msi* file, è necessario eseguire **devenv /setup** come parte dell'installazione nell'ordine individuare le estensioni di Visual Studio.

> [!NOTE]
>  Le informazioni in questo argomento si applicano all'individuazione *devenv.exe* con Visual Studio 2008 e versioni precedenti. Per informazioni su come individuare *devenv.exe* con le versioni successive di Visual Studio, vedere [requisiti di sistema di rilevare](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Trovare devenv.exe
 È possibile trovare ogni versione *devenv.exe* dal Registro di sistema i valori necessari [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] scrivere programmi di installazione, usando la tabella di RegLocator e AppSearch tabelle per archiviare i valori del Registro di sistema come proprietà. Per altre informazioni, vedere [rileva i requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator righe della tabella per individuare devenv.exe da diverse versioni di Visual Studio

|Signature|Radice|Chiave|nome|Tipo|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Righe della tabella AppSearch per le righe della tabella corrispondente RegLocator

|Proprietà|Signature|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Ad esempio, il programma di installazione di Visual Studio scrive il valore del Registro di sistema del **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** come *C:\VS2008\Common7\IDE\devenv.exe*, un percorso completo del file eseguibile deve essere eseguito il programma di installazione.

> [!NOTE]
> Poiché la colonna di tipo della tabella RegLocator è 2, non è necessario specificare informazioni aggiuntive sulla versione nella tabella di firma.

## <a name="run-devenvexe"></a>Eseguire devenv.exe
 Dopo aver AppSearch azione standard viene eseguito nel programma di installazione, ogni proprietà nella tabella AppSearch ha un valore che punta al *devenv.exe* file per la versione corrispondente di Visual Studio. Se uno dei valori del Registro di sistema non sono presente, perché non è installata la versione di Visual Studio, ovvero la proprietà specificata è impostata su null.

 Programma di installazione di Windows supporta l'esecuzione di un eseguibile a cui fa riferimento una proprietà tramite un'azione personalizzata digita 50. L'azione personalizzata deve includere le opzioni di esecuzione di script, `msidbCustomActionTypeInScript` (da 1024) e `msidbCustomActionTypeCommit` (512), per garantire che il pacchetto VSPackage è stato installato correttamente prima dell'integrazione in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [tabella CustomAction](https://docs.microsoft.com/windows/desktop/msi/customaction-table) e [opzioni di esecuzione di negli script di azione personalizzata](https://docs.microsoft.com/windows/desktop/msi/custom-action-in-script-execution-options).

 Azioni personalizzate di tipo 50 specificano la proprietà che contiene il file eseguibile come il valore della colonna di origine e gli argomenti della riga di comando nella colonna di destinazione.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Righe della tabella CustomAction eseguire devenv.exe

|Operazione|Tipo|Origine|destinazione|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 Azioni personalizzate devono essere create nella tabella InstallExecuteSequence pianificarli per l'esecuzione durante l'installazione. Usare la proprietà corrispondente in ogni riga della colonna della condizione per evitare che l'azione personalizzata in esecuzione se tale versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non è installato nel sistema.

> [!NOTE]
>  Proprietà con valori null restituiscono `False` quando utilizzata nelle condizioni.

 Il valore della colonna della sequenza per ogni azione personalizzata dipende da altri valori di sequenza nel pacchetto di Windows Installer. I valori di sequenza devono essere in modo che il *devenv.exe* azioni personalizzate runas vicino possibile a immediatamente prima dell'azione standard InstallFinalize mentre.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Nella tabella per pianificare le azioni personalizzate devenv.exe InstallExecuteSequence

|Operazione|Condizione|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Vedere anche
- [Installare i pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
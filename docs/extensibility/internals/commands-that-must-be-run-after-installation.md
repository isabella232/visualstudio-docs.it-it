---
title: Comandi che devono essere eseguiti dopo l'| Microsoft Docs
description: Informazioni sui comandi che devono essere eseguiti come parte dell'installazione di un'estensione distribuita tramite un file .msi in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9038fafaccef8d73b15684fef8d425645ab55dcf6296487fa4993685dc5a17ea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401498"
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandi che devono essere eseguiti dopo l'installazione
Se si distribuisce l'estensione tramite un file *.msi,* è necessario eseguire **devenv /setup** come parte dell'installazione per consentire Visual Studio individuare le estensioni.

> [!NOTE]
> Le informazioni contenute in questo argomento si applicano alla *ricercadevenv.exe* con Visual Studio 2008 e versioni precedenti. Per informazioni su come individuare *devenv.exe* con le versioni successive di Visual Studio, vedere [Rilevare i requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Trovare devenv.exe
 È possibile individuare i  valoridevenv.exedi ogni versione dai valori del Registro di sistema che i programmi di installazione scrivono usando la tabella RegLocator e le tabelle AppSearch per archiviare i valori del Registro di sistema [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] come proprietà. Per altre informazioni, vedere [Rilevare i requisiti di sistema.](../../extensibility/internals/detecting-system-requirements.md)

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Righe della tabella RegLocator per individuare devenv.exe da versioni diverse di Visual Studio

|Firma|Radice|Codice|Nome|Tipo|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Righe della tabella AppSearch per le righe della tabella RegLocator corrispondenti

|Proprietà|Firma|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Ad esempio, il programma di Visual Studio scrive il valore del Registro di sistema **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** come *C:\VS2008\Common7\IDE\devenv.exe*, un percorso completo del file eseguibile che deve essere eseguito dal programma di installazione.

> [!NOTE]
> Poiché la colonna Type della tabella RegLocator è 2, non è necessario specificare informazioni aggiuntive sulla versione nella tabella Signature.

## <a name="run-devenvexe"></a>Eseguire devenv.exe
 Dopo l'esecuzione dell'azione standard AppSearch nel programma di installazione, ogni proprietà nella tabella AppSearch ha un valore che punta al file *devenv.exe* per la versione corrispondente di Visual Studio. Se uno dei valori del Registro di sistema specificati non è presente, perché la versione di Visual Studio non è installata, la proprietà specificata viene impostata su Null.

 Windows Il programma di installazione supporta l'esecuzione di un eseguibile a cui una proprietà punta tramite il tipo di azione personalizzata 50. L'azione personalizzata deve includere le opzioni di esecuzione nello script `msidbCustomActionTypeInScript` (1024) e `msidbCustomActionTypeCommit` (512) per assicurarsi che il pacchetto VSPackage sia stato installato correttamente prima di integrarlo in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Per altre informazioni, vedere [Tabella CustomAction](/windows/desktop/msi/customaction-table) e [Opzioni di esecuzione in script dell'azione personalizzata](/windows/desktop/msi/custom-action-in-script-execution-options).

 Le azioni personalizzate di tipo 50 specificano la proprietà contenente l'eseguibile come valore della colonna Source e degli argomenti della riga di comando nella colonna Target.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Righe della tabella CustomAction da eseguire devenv.exe

|Azione|Tipo|Source (Sorgente)|Destinazione|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 Le azioni personalizzate devono essere scritte nella tabella InstallExecuteSequence per pianificarle per l'esecuzione durante l'installazione. Usare la proprietà corrispondente in ogni riga della colonna Condizione per impedire l'esecuzione dell'azione personalizzata se tale versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non è installata nel sistema.

> [!NOTE]
> Le proprietà con valori Null restituiscono se `False` usate nelle condizioni.

 Il valore della colonna Sequenza per ogni azione personalizzata dipende da altri valori di sequenza nel pacchetto Windows installer. I valori di sequenza devono essere tali *che* devenv.exeazioni personalizzate vengono eseguite il più vicino possibile a immediatamente prima dell'azione standard InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabella InstallExecuteSequence per pianificare le devenv.exe personalizzate

|Azione|Condition|Sequenza|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Vedi anche
- [Installare i pacchetti VSPackage con il Windows di installazione](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

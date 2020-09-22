---
title: Comandi che devono essere eseguiti dopo l'installazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 158119759f8e90161e1f3b5267be498dfc1c9b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840075"
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandi da eseguire dopo l'installazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Se si distribuisce l'estensione tramite un file con estensione msi, è necessario eseguire `devenv /setup` come parte dell'installazione per consentire a Visual Studio di individuare le estensioni.  
  
> [!NOTE]
> Le informazioni contenute in questo argomento si applicano alla ricerca di DevEnv con Visual Studio 2008 e versioni precedenti. Per informazioni su come individuare DevEnv con versioni successive di Visual Studio, vedere [rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Ricerca di devenv.exe  
 È possibile individuare devenv.exe di ogni versione dai valori del registro di sistema [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] scritti dai programmi di installazione, usando la tabella RegLocator e la tabella AppSearch per archiviare i valori del registro di sistema come proprietà. Per ulteriori informazioni, vedere [rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator righe della tabella per individuare devenv.exe da versioni diverse di Visual Studio  
  
|Signature_|Radice|Codice|Nome|Type|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Righe della tabella AppSearch per le righe della tabella RegLocator corrispondenti  
  
|Proprietà|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Ad esempio, il programma di installazione di Visual Studio scrive il valore del registro di sistema di **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\9.0\setup\vs\environmentpath** come **C:\VS2008\Common7\IDE\devenv.exe**, un percorso completo dell'eseguibile che deve essere eseguito dal programma di installazione.  
  
 **Nota** Poiché la colonna di tipo RegLocator è 2, non è necessario specificare ulteriori informazioni sulla versione nella tabella della firma.  
  
## <a name="running-devenvexe"></a>Esecuzione di devenv.exe  
 Dopo l'esecuzione dell'azione standard AppSearch nel programma di installazione, ogni proprietà nella tabella AppSearch ha un valore che punta al file devenv.exe per la versione corrispondente di Visual Studio. Se uno dei valori del registro di sistema specificato non è presente, perché la versione di Visual Studio non è installata, la proprietà specificata è impostata su null.  
  
 Windows Installer supporta l'esecuzione di un eseguibile a cui fa riferimento una proprietà con tipo di azione personalizzata 50. L'azione personalizzata deve includere le opzioni di esecuzione nello script, msidbCustomActionTypeInScript (1024) e msidbCustomActionTypeCommit (512), per garantire che il pacchetto VSPackage sia stato installato correttamente prima di integrarlo in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Per ulteriori informazioni, vedere la tabella CustomAction e le opzioni di esecuzione in-script dell'azione personalizzata.  
  
 Le azioni personalizzate di tipo 50 specificano la proprietà che contiene il file eseguibile come valore della colonna di origine e gli argomenti della riga di comando nella colonna di destinazione.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction righe della tabella da eseguire devenv.exe  
  
|Azione|Type|Source (Sorgente)|Destinazione|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Le azioni personalizzate devono essere create nella tabella InstallExecuteSequence per pianificarne l'esecuzione durante l'installazione. Utilizzare la proprietà corrispondente in ogni riga della colonna Condition per impedire l'esecuzione dell'azione personalizzata se tale versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] non è installata nel sistema.  
  
> [!NOTE]
> `Null` le proprietà restituiscono `False` quando vengono utilizzate in condizioni.  
  
 Il valore della colonna sequenza per ogni azione personalizzata dipende da altri valori di sequenza nel pacchetto di Windows Installer. I valori della sequenza devono essere in modo che le azioni personalizzate devenv.exe vengano eseguite il più vicino possibile a immediatamente prima dell'azione standard InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabella InstallExecuteSequence per pianificare le azioni personalizzate devenv.exe  
  
|Azione|Condizione|Sequenza|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

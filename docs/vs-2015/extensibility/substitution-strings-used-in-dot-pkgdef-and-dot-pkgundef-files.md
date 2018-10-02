---
title: Usato nelle stringhe di sostituzione. Pkgdef e. File Pkgundef | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24996e4e32ab86af46fce5280947719f906ffc3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532177"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Usato nelle stringhe di sostituzione. Pkgdef e. File Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [le stringhe di sostituzione usate in. Pkgdef e. File Pkgundef](https://docs.microsoft.com/visualstudio/extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files).  
  
È possibile usare le stringhe di sostituzione elencate di seguito nel pkgdef e pkgundef file definiti per Visual Studio applicazione shell isolata.  
  
## <a name="substitution-strings"></a>Stringhe di sostituzione  
  
|Stringa|Descrizione|  
|------------|-----------------|  
|$=*Registro*$|Il valore della *registro* voce. Se la stringa della voce del Registro di sistema termina con una barra rovesciata (\\), viene usato il valore predefinito della sottochiave del Registro di sistema. Ad esempio, la sostituzione stringa $= HKEY_CURRENT_USER\Environment\TEMP$ viene espanso nella cartella temporanea dell'utente corrente.|  
|$ $AppName|Il nome completo dell'applicazione che viene passato per i punti di ingresso AppEnv.dll. Il nome completo è costituito da un carattere di sottolineatura, il nome dell'applicazione e l'identificatore di classe (CLSID) dell'oggetto di automazione dell'applicazione, viene anche registrato come valore dell'impostazione ThisVersionDTECLSID nel file con estensione pkgdef di progetto.|  
|$AppDataLocalFolder|Nella sottocartella in % LOCALAPPDATA % per l'applicazione.|  
|$ $BaseInstallDir|Il percorso completo della posizione in cui è stato installato Visual Studio.|  
|$ $CommonFiles|Il valore della variabile di ambiente % CommonProgramFiles %.|  
|$ $MyDocuments|Il percorso completo della cartella documenti dell'utente corrente.|  
|$ $PackageFolder|Il percorso completo della directory che contiene i file di assembly del pacchetto dell'applicazione.|  
|$ $ProgramFiles|Il valore della variabile di ambiente % ProgramFiles %.|  
|$ $RootFolder|Il percorso completo della directory radice dell'applicazione.|  
|$ $RootKey|La chiave del Registro di sistema radice per l'applicazione. Per impostazione predefinita la radice è HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* (quando l'applicazione è in esecuzione, _Config viene aggiunto a questa chiave). È impostato dal valore RegistryRoot nella *SolutionName*file pkgdef.<br /><br /> La stringa $ $RootKey utilizzabile per recuperare un valore del Registro di sistema nella sottochiave dell'applicazione. Ad esempio, la stringa "$= $RootKey$ \AppIcon$" restituirà il valore della voce AppIcon nella sottochiave della radice dell'applicazione.<br /><br /> Il parser elabora il file pkgdef in modo sequenziale e può accedere a una voce del Registro di sistema nella sottochiave applicazione solo se la voce è stata definita in precedenza|  
|$ $ShellFolder|Il percorso completo della posizione in cui è stato installato Visual Studio.|  
|$ $System|Nella cartella Windows\system32.|  
|$ $WINDIR|La cartella Windows.|  
  
 Se il parser non riconosce la stringa di sostituzione o non sia possibile determinare il valore di una voce del Registro di sistema o una variabile di ambiente, quindi non viene eseguita la sostituzione su quella parte della stringa.


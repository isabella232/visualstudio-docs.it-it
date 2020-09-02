---
title: Stringhe di sostituzione utilizzate in. Pkgdef e. File Pkgundef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160543"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Stringhe di sostituzione usate nei file con estensione pkgdef e pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare le stringhe di sostituzione elencate di seguito nei file con estensione pkgdef e pkgundef definiti per l'applicazione Visual Studio Isolated Shell.  
  
## <a name="substitution-strings"></a>Stringhe di sostituzione  
  
|Stringa|Descrizione|  
|------------|-----------------|  
|$=*RegistryEntry*$|Valore della voce *RegistryEntry* . Se la stringa di voce del registro di sistema termina con una barra rovesciata ( \\ ), viene usato il valore predefinito della sottochiave del registro di sistema. La stringa di sostituzione $ = HKEY_CURRENT_USER \Environment\TEMP $ viene ad esempio espansa nella cartella temporanea dell'utente corrente.|  
|$AppName $|Nome completo dell'applicazione passata ai punti di ingresso AppEnv.dll. Il nome completo è costituito dal nome dell'applicazione, da un carattere di sottolineatura e dall'identificatore di classe (CLSID) dell'oggetto di automazione dell'applicazione, che viene anche registrato come valore dell'impostazione ThisVersionDTECLSID nel file Project. pkgdef.|  
|$AppDataLocalFolder|Sottocartella in% LOCALAPPDATA% per questa applicazione.|  
|$BaseInstallDir $|Percorso completo della posizione in cui è stato installato Visual Studio.|  
|$CommonFiles $|Valore della variabile di ambiente% CommonProgramFiles%.|  
|$MyDocuments $|Percorso completo della cartella documenti dell'utente corrente.|  
|$PackageFolder $|Percorso completo della directory che contiene i file di assembly del pacchetto per l'applicazione.|  
|$ProgramFiles $|Valore della variabile di ambiente% ProgramFiles%.|  
|$RootFolder $|Percorso completo della directory radice dell'applicazione.|  
|$RootKey $|Chiave del registro di sistema radice per l'applicazione. Per impostazione predefinita, la radice si trova in HKEY_CURRENT_USER \SOFTWARE \\ *CompanyName* \\ *NomeProgetto* \\ *VersionNumber* (quando l'applicazione è in esecuzione, _Config viene accodata a questa chiave). Viene impostato dal valore RegistryRoot nel file *SolutionName*. pkgdef.<br /><br /> La stringa $RootKey $ può essere usata per recuperare un valore del registro di sistema nella sottochiave dell'applicazione. Ad esempio, la stringa "$ = $RootKey $ \AppIcon $" restituirà il valore della voce AppIcon sotto la sottochiave radice dell'applicazione.<br /><br /> Il parser elabora il file con estensione pkgdef in modo sequenziale e può accedere a una voce del registro di sistema nella sottochiave dell'applicazione solo se la voce è stata definita in precedenza|  
|$ShellFolder $|Percorso completo della posizione in cui è stato installato Visual Studio.|  
|$System $|Cartella Windows\System32.|  
|$WINDIR $|Cartella di Windows.|  
  
 Se il parser non riconosce la stringa di sostituzione oppure non è in grado di determinare il valore di una voce del registro di sistema o di una variabile di ambiente, non esegue la sostituzione sulla parte della stringa.

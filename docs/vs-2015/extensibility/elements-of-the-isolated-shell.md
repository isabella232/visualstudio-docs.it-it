---
title: Elementi della shell isolata | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204606"
---
# <a name="elements-of-the-isolated-shell"></a>Elementi della shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare le impostazioni del registro di sistema, le impostazioni della fase di esecuzione e il punto di ingresso dell'applicazione dell'applicazione shell isolata e i relativi file. vsct,. pkgdef e. pkgundef.  
  
## <a name="registry-settings"></a>Impostazioni del Registro di sistema  
 Entrambi i file con estensione pkgdef e pkgundef modificano le impostazioni del registro di sistema per l'applicazione shell isolata. Quando l'applicazione viene eseguita, le impostazioni del registro di sistema sono definite nella sequenza seguente:  
  
 Quando l'applicazione viene eseguita, le impostazioni del registro di sistema sono definite nella sequenza seguente:  
  
1. Viene creata la chiave del registro di sistema per l'applicazione.  
  
2. Il registro di sistema viene aggiornato dal file con estensione pkgdef dell'applicazione definendo le chiavi e le voci specificate.  
  
3. Per ogni pacchetto che fa parte dell'applicazione, il registro di sistema viene aggiornato dal file con estensione pkgdef del pacchetto. Ogni pacchetto viene definito nel file con estensione pkgdef dell'applicazione dalla chiave $RootKey $ \Packages \\ {*vsPackageGuid*} per il pacchetto.  
  
4. Il registro di sistema viene aggiornato da AppEnvConfig. pkgdef e BaseConfig. pkgdef nella directory *percorso di installazione di Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform. Questi file fanno parte di Visual Studio e fanno parte anche del pacchetto ridistribuibile di Visual Studio Shell (modalità isolata).  
  
5. Il registro di sistema viene aggiornato dal file con estensione pkgundef dell'applicazione rimuovendo le chiavi e le voci specificate.  
  
## <a name="run-time-settings"></a>Impostazioni della fase di esecuzione  
 Quando un utente avvia l'applicazione shell isolata, chiama il punto di ingresso iniziale della shell di Visual Studio. Le impostazioni dell'applicazione vengono definite all'avvio dell'applicazione, come indicato di seguito:  
  
1. La shell di Visual Studio controlla la presenza di chiavi specifiche nel registro di sistema dell'applicazione. Se l'impostazione per una chiave viene specificata nella chiamata al punto di ingresso iniziale, tale valore esegue l'override del valore nel registro di sistema.  
  
2. Se il registro di sistema o il parametro del punto di ingresso non specificano il valore di un'impostazione, viene usato il valore predefinito per l'impostazione.  
  
   Quando un utente avvia l'applicazione dalla riga di comando, tutte le opzioni della riga di comando vengono passate alla shell di Visual Studio, che le gestisce esattamente come devenv. Per ulteriori informazioni sulle opzioni devenv, vedere [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md) e [Opzioni della riga di comando devenv per lo sviluppo di VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Per ulteriori informazioni sulla modalità di registrazione di un pacchetto per le opzioni della riga di comando, vedere [aggiunta di opzioni della riga di comando](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Punto di ingresso iniziale  
 Il file di Appenvstub.dll contiene punti di ingresso per l'accesso alla shell isolata. All'avvio dell'applicazione, viene chiamato il punto di ingresso iniziale di Appenvstub.dll.  
  
 È possibile modificare il comportamento dell'applicazione modificando il valore dell'ultimo parametro passato al punto di ingresso iniziale. Per altre informazioni, vedere [parametri del punto di ingresso della shell isolata (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Il. File vsct  
 Il file con estensione vsct consente di specificare quali elementi standard dell'interfaccia utente di Visual Studio sono disponibili nell'applicazione. Per ulteriori informazioni, vedere [. File vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Il. File Pkgundef  
 Quando l'applicazione viene installata in un computer in cui è già installato Visual Studio, viene creata una copia delle voci del registro di sistema di Visual Studio per l'applicazione. Per impostazione predefinita, l'applicazione usa VSPackage già installati nel computer. Il file con estensione pkgundef consente di escludere le voci del registro di sistema per rimuovere elementi specifici della shell di Visual Studio o delle estensioni dall'applicazione. Per ulteriori informazioni, vedere [. File Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Il file con estensione pkgundef consente di escludere le voci del registro di sistema per rimuovere elementi specifici della shell di Visual Studio o delle estensioni dall'applicazione. Per ulteriori informazioni, vedere [. File Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Il set di GUID di pacchetto che è possibile escludere è elencato in [GUID di pacchetto delle funzionalità di Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>Il. File pkgdef  
 Il file con estensione pkgdef consente di definire le voci del registro di sistema per l'applicazione che vengono impostate durante l'installazione dell'applicazione. Per una descrizione del file con estensione pkgdef e un elenco di voci del registro di sistema utilizzate dalla shell di Visual Studio, vedere [. File pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Stringhe di sostituzione  
 Le stringhe di sostituzione utilizzate nei file con estensione pkgdef e pkgundef sono elencate in [stringhe di sostituzione utilizzate in. Pkgdef e. File Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Altre impostazioni  
 Se l'applicazione della shell isolata dipende da Microsoft.VisualStudio.GraphModel.dll, è necessario aggiungere il reindirizzamento di binding seguente al file. config dell'applicazione shell isolata:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```

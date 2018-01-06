---
title: Gli elementi della Shell isolata | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 82379a840010ebae434f8ad1a03c12793fe10ec5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="elements-of-the-isolated-shell"></a>Elementi della Shell isolata
È possibile modificare il punto di ingresso dell'applicazione di applicazione shell isolata e vsct,. pkgdef, and.pkgundef file, impostazioni del Registro di sistema e le impostazioni di runtime.  
  
## <a name="registry-settings"></a>Impostazioni Registro di sistema  
 Sia il pkgdef e i file .pkgundef modificano le impostazioni del Registro di sistema per l'applicazione shell isolata. Quando l'applicazione viene eseguita, le impostazioni del Registro di sistema sono definite nella sequenza seguente:  
  
 Quando l'applicazione viene eseguita, le impostazioni del Registro di sistema sono definite nella sequenza seguente:  
  
1.  La chiave del Registro di sistema per l'applicazione viene creata.  
  
2.  Il Registro di sistema viene aggiornato dal file. pkgdef dell'applicazione mediante la definizione di voci e chiavi specificate.  
  
3.  Per ogni pacchetto che fa parte dell'applicazione, il Registro di sistema viene aggiornato dal file. pkgdef dello stesso pacchetto. Ogni pacchetto è definito nel file. pkgdef dell'applicazione per il \Packages $ $RootKey\\{*vsPackageGuid*} chiave per il pacchetto.  
  
4.  Il Registro di sistema viene aggiornato dal AppEnvConfig.pkgdef e BaseConfig.pkgdef nel *il percorso di installazione di Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform directory. Questi file sono parte di Visual Studio e far parte del pacchetto ridistribuibile Visual Studio Shell (modalità isolata).  
  
5.  Il Registro di sistema viene aggiornato dal file dell'applicazione .pkgundef rimuovendo le voci e chiavi specificate.  
  
## <a name="run-time-settings"></a>Impostazioni di Run-Time  
 Quando un utente avvia l'applicazione shell isolata, chiama il punto di ingresso di avvio di shell di Visual Studio. Le impostazioni dell'applicazione sono definite all'avvio dell'applicazione, come indicato di seguito:  
  
1.  La shell di Visual Studio consente di controllare il Registro di sistema per le chiavi specifiche. Se l'impostazione per una chiave viene specificato nella chiamata al punto di ingresso di avvio, tale valore sostituirà il valore del Registro di sistema.  
  
2.  Se il Registro di sistema né la voce punto parametro specifica il valore di un'impostazione, quindi viene utilizzato il valore predefinito per l'impostazione.  
  
 Quando un utente avvia l'applicazione dalla riga di comando, tutte le opzioni della riga di comando vengono passate alla shell di Visual Studio, che li gestisce nello stesso modo in cui vengono effettuate. Per ulteriori informazioni sulle opzioni di Devenv, vedere [opzioni della riga di comando Devenv](../../ide/reference/devenv-command-line-switches.md) e [opzioni della riga di comando Devenv per lo sviluppo di VSPackage](../devenv-command-line-switches-for-vspackage-development.md). Per ulteriori informazioni sulla modalità della registrazione di un pacchetto per opzioni della riga di comando, vedere [aggiunta di parametri della riga di comando](../adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Il punto di ingresso di avvio  
 Il file Appenvstub.dll contiene punti di ingresso per l'accesso alle shell isolata. All'avvio dell'applicazione, viene chiamato punto di ingresso iniziale di Appenvstub.dll.  
  
 È possibile modificare il comportamento dell'applicazione modificando il valore dell'ultimo parametro che viene passato al punto di ingresso di inizio. Per ulteriori informazioni, vedere [isolato Shell voce punto parametri (C++)](isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Il file con estensione File Vsct  
 Il file con estensione vsct consente di specificare quali elementi dell'interfaccia utente di Visual Studio standard sono disponibili nell'applicazione. Per ulteriori informazioni, vedere [. File Vsct](modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Il file con estensione File Pkgundef  
 Quando l'applicazione è installata in un computer in cui è già installato Visual Studio, viene creata una copia delle voci del Registro di sistema di Visual Studio per l'applicazione. Per impostazione predefinita, l'applicazione utilizza pacchetti VSPackage che sono già installati nel computer. Il file .pkgundef consente di escludere le voci del Registro di sistema per rimuovere gli elementi specifici della shell di Visual Studio o estensioni dall'applicazione. Per ulteriori informazioni, vedere [. File Pkgundef](modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Il file .pkgundef consente di escludere le voci del Registro di sistema per rimuovere gli elementi specifici della shell di Visual Studio o estensioni dall'applicazione. Per ulteriori informazioni, vedere [. File Pkgundef](modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Il set di GUID che è possibile escludere pacchetto sono elencati [pacchetto GUID di funzionalità di Visual Studio](package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>Il file con estensione File pkgdef  
 Il file. pkgdef consente di definire le voci del Registro di sistema per l'applicazione che vengono impostate durante l'installazione dell'applicazione. Per una descrizione del file. pkgdef e un elenco di voci del Registro di sistema che utilizza la shell di Visual Studio, vedere [. File pkgdef](modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Stringhe di sostituzione  
 Le stringhe di sostituzione usate nei file. pkgdef e .pkgundef sono elencate [sostituzione utilizzare stringhe. Pkgdef e. File Pkgundef](substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Altre impostazioni  
 Se l'applicazione shell isolata dipende da Microsoft.VisualStudio.GraphModel.dll, è necessario aggiungere il seguente reindirizzamento dell'associazione al file config dell'applicazione Shell isolata:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
---
title: Gli elementi della Shell isolata | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca63b6a8c973b33a9dffc98966fd0622c0a5407a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868430"
---
# <a name="elements-of-the-isolated-shell"></a>Elementi della Shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare le impostazioni del Registro di sistema, le impostazioni di runtime e punto di ingresso dell'applicazione dell'applicazione shell isolata e relativo vsct, con estensione pkgdef, and.pkgundef file.  
  
## <a name="registry-settings"></a>Impostazioni Registro di sistema  
 Sia il con estensione pkgdef e i file con estensione pkgundef modificano le impostazioni del Registro di sistema per l'applicazione shell isolata. Quando viene eseguita l'applicazione, le impostazioni del Registro di sistema sono definite nella sequenza seguente:  
  
 Quando viene eseguita l'applicazione, le impostazioni del Registro di sistema sono definite nella sequenza seguente:  
  
1.  La chiave del Registro di sistema per l'applicazione viene creata.  
  
2.  Il Registro di sistema viene aggiornato dal file con estensione pkgdef dell'applicazione mediante la definizione di voci e chiavi specificate.  
  
3.  Per ogni pacchetto che fa parte dell'applicazione, il Registro di sistema viene aggiornato dal file con estensione pkgdef dello stesso pacchetto. Ogni pacchetto è definito nel file con estensione pkgdef dell'applicazione per il \Packages $ $RootKey\\{*vsPackageGuid*} chiave per il pacchetto.  
  
4.  Il Registro di sistema viene aggiornato dal AppEnvConfig.pkgdef e BaseConfig.pkgdef nel *percorso di installazione di Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform directory. Questi file sono parte di Visual Studio e far parte del pacchetto ridistribuibile Visual Studio Shell (modalità isolata).  
  
5.  Il Registro di sistema viene aggiornato dal file con estensione pkgundef dell'applicazione rimuovendo le voci e chiavi specificate.  
  
## <a name="run-time-settings"></a>Impostazioni di Run-Time  
 Quando un utente avvia l'applicazione shell isolata, chiama il punto di ingresso di avvio della shell di Visual Studio. Le impostazioni dell'applicazione sono definite all'avvio dell'applicazione, come indicato di seguito:  
  
1. La shell di Visual Studio controlla il Registro di sistema dell'applicazione per le chiavi specifiche. Se l'impostazione per una chiave viene specificato nella chiamata al punto di ingresso di avvio, tale valore sostituisce il valore del Registro di sistema.  
  
2. Se il Registro di sistema né la voce punto parametro specifica il valore di un'impostazione, quindi viene usato il valore predefinito per l'impostazione.  
  
   Quando un utente avvia l'applicazione dalla riga di comando, tutte le opzioni della riga di comando vengono passate alla shell di Visual Studio, che li gestisce nella stesso modo in cui vengono effettuate. Per altre informazioni sulle opzioni Devenv, vedere [opzioni della riga di comando Devenv](../ide/reference/devenv-command-line-switches.md) e [opzioni della riga di comando Devenv per lo sviluppo di VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Per altre informazioni sul modo in cui si registra un pacchetto per opzioni della riga di comando, vedere [aggiunta di opzioni della riga di comando](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Il punto di ingresso di avvio  
 Il file Appenvstub.dll contiene punti di ingresso per l'accesso alle shell isolata. All'avvio dell'applicazione, viene chiamato punto di ingresso iniziale di Appenvstub.dll.  
  
 È possibile modificare il comportamento dell'applicazione modificando il valore dell'ultimo parametro che viene passato al punto di ingresso iniziale. Per altre informazioni, vedere [isolato Shell voce punto parametri (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Il file con estensione File Vsct  
 Il file con estensione vsct consente di specificare quali elementi dell'interfaccia utente di Visual Studio standard sono disponibili nell'applicazione. Per altre informazioni, vedere [. File Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Il file con estensione File Pkgundef  
 Quando l'applicazione viene installata in un computer in cui è già installato Visual Studio, viene creata una copia delle voci del Registro di sistema di Visual Studio per l'applicazione. Per impostazione predefinita, l'applicazione usa i pacchetti VSPackage che sono già installati nel computer. Il file con estensione pkgundef consente di escludere le voci del Registro di sistema per rimuovere elementi specifici della shell di Visual Studio o estensioni dall'applicazione. Per altre informazioni, vedere [. File Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Il file con estensione pkgundef consente di escludere le voci del Registro di sistema per rimuovere elementi specifici della shell di Visual Studio o estensioni dall'applicazione. Per altre informazioni, vedere [. File Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Il set di pacchetti GUID che è possibile escludere sono racchiusi [pacchetto i GUID di funzionalità di Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>Il file con estensione File pkgdef  
 Il file con estensione pkgdef consente di definire le voci del Registro di sistema per l'applicazione che vengono impostate quando l'applicazione viene installata. Per una descrizione del file con estensione pkgdef e un elenco di voci del Registro di sistema che utilizza la shell di Visual Studio, vedere [. I file pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Stringhe di sostituzione  
 Le stringhe di sostituzione usate nei file con estensione pkgdef e pkgundef sono elencate [le stringhe di sostituzione usate in. Pkgdef e. File Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Altre impostazioni  
 Se l'applicazione shell isolata dipende Microsoft.VisualStudio.GraphModel.dll, è necessario aggiungere il seguente reindirizzamento dell'associazione al file. config dell'applicazione Shell isolata:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```


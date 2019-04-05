---
title: Supporto per la persistenza dello stato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969987"
---
# <a name="support-for-state-persistence"></a>Supporto per la persistenza dello stato
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] può gestire lo stato degli oggetti più comuni. Ad esempio, le proprietà di soluzione e progetto sono salvate e ripristinate dal file di soluzione e progetto. Impostazioni utente possono essere esportate e importate dai file di impostazioni.  
  
 I pacchetti VSPackage in genere si basano sull'archiviazione locale, nel Registro di sistema o nella cartella di dati dell'applicazione per l'utente corrente o computer. I valori che richiedono una piccola quantità di spazio di archiviazione, ad esempio numeri interi e stringhe, vengono in genere archiviati nel Registro di sistema. I valori che richiedono una grande quantità di spazio di archiviazione, ad esempio le bitmap, vengono salvati in un file. Stesso il percorso del file può essere salvato nel Registro di sistema. Il meccanismo di persistenza è necessario disporre dell'autorizzazione per accedere all'archiviazione locale.  
  
## <a name="support-for-locating-local-storage"></a>Supporto per l'individuazione di archiviazione locale  
 Il <xref:Microsoft.VisualStudio.Shell.Package> classe offre supporto per l'individuazione delle informazioni sullo stato nella cartella della data del Registro di sistema o un'applicazione di sistema per l'utente corrente o computer.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Restituisce il percorso della radice del Registro di sistema del computer locale per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ad esempio, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0Exp.  
  
 La radice del Registro di sistema locale viene ottenuta dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> servizio. Se questo non è disponibile, esso viene ottenuto dal <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> attributo del pacchetto VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Restituisce il percorso (per computer) dell'utente corrente radice del Registro di sistema per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ad esempio, HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp.  
  
 La radice del Registro di sistema locale viene ottenuta dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> servizio. Se questo non è disponibile, viene ottenuta dall'attributo DefaultLocalRegistryRoot del pacchetto VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Restituisce il percorso della directory usata come repository comune dei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i dati per l'utente roaming corrente, ad esempio, C:\Documents and Settings\\*YourAccountName*\Application VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Restituisce il percorso della directory usata come repository comune dei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i dati corrente non connessi a utente, ad esempio, C:\Documents and Settings \\\*YourAccountName*Settings\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>Vedere anche  
 [Stato di un pacchetto VSPackage](../misc/vspackage-state.md)
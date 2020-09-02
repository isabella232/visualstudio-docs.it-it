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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434319"
---
# <a name="support-for-state-persistence"></a>Supporto per la persistenza dello stato
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di mantenere lo stato degli oggetti comuni. Ad esempio, le proprietà della soluzione e del progetto vengono salvate e ripristinate dai file di soluzione e di progetto. Le impostazioni utente possono essere esportate e importate dai file di impostazioni.  
  
 I pacchetti VSPackage si basano in genere sull'archiviazione locale, nel registro di sistema o nella cartella Application Data per l'utente o il computer corrente. I valori che richiedono una piccola quantità di spazio per l'archiviazione, ad esempio numeri interi e stringhe, vengono in genere archiviati nel registro di sistema. I valori che richiedono molto spazio per l'archiviazione, ad esempio le bitmap, vengono salvati in un file. Il percorso del file può essere salvato nel registro di sistema. Il meccanismo di persistenza deve disporre dell'autorizzazione per accedere alla risorsa di archiviazione locale.  
  
## <a name="support-for-locating-local-storage"></a>Supporto per l'individuazione dell'archiviazione locale  
 La <xref:Microsoft.VisualStudio.Shell.Package> classe fornisce supporto per l'individuazione delle informazioni sullo stato nella cartella registro di sistema o dati applicazione per l'utente o il computer corrente.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Restituisce il percorso della radice del registro di sistema del computer locale per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ad esempio HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\8.0Exp.  
  
 La radice del registro di sistema locale viene ottenuta dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> servizio. Se non è disponibile, viene ottenuto dall' <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> attributo del pacchetto VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Restituisce il percorso della radice del registro di sistema dell'utente corrente (per computer) per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ad esempio HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp.  
  
 La radice del registro di sistema locale viene ottenuta dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> servizio. Se non è disponibile, viene ottenuto dall'attributo DefaultLocalRegistryRoot del pacchetto VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Restituisce il percorso della directory che funge da repository comune per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i dati dell'utente comune corrente, ad esempio C:\Documents and Settings \\ *i*\Dati Data\Microsoft\VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Restituisce il percorso della directory che funge da repository comune per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i dati per l'utente non roaming corrente, ad esempio C:\Documents and Settings \\ *i*\Impostazioni locali\Dati Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>Vedere anche  
 [Stato di un pacchetto VSPackage](../misc/vspackage-state.md)
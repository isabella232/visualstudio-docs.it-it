---
title: Specifica il percorso di File VSPackage nella shell di Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d7abb72d3d577c4870030c76f87f0a41f133480
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964240"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Definizione del percorso di file VSPackage nella shell di Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] deve essere in grado di individuare l'assembly DLL per caricare il pacchetto VSPackage. È possibile individuarlo in vari modi, come descritto nella tabella seguente.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|Usare la chiave del Registro di sistema di base di codici.|La chiave CodeBase può essere utilizzata per indirizzare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per caricare l'assembly VSPackage da qualsiasi percorso completo del file. Il valore della chiave deve essere il percorso del file della DLL. Questo è il modo migliore per avere [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] carica l'assembly del pacchetto. Questa tecnica è detta anche "CodeBase/privata installazione directory tecnica." Durante la registrazione viene passato il valore della codebase alle classi di attributo di registrazione tramite un'istanza di <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> tipo.|  
|Collocare la DLL nel **PrivateAssemblies** directory.|Inserire l'assembly nel **PrivateAssemblies** sottodirectory del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] directory. Gli assembly che si trovano **PrivateAssemblies** vengono rilevate automaticamente, ma non sono visibili nel **Aggiungi riferimenti** nella finestra di dialogo. La differenza tra **PrivateAssemblies** e **PublicAssemblies** è che gli assembly nel **PublicAssemblies** vengono enumerati nel **Aggiungi riferimenti**  nella finestra di dialogo. Se si sceglie di non usare la tecnica di "directory di installazione di base di codici/privata", quindi è necessario installare nel **PrivateAssemblies** directory.|  
|Usare un assembly con nome sicuro e la chiave del Registro di sistema Assembly.|La chiave di Assembly può essere utilizzata per indirizzare in modo esplicito [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per caricare un nome sicuro denominato assembly VSPackage. Il valore della chiave deve essere il nome sicuro dell'assembly.|  
|Collocare la DLL nel **PublicAssemblies** directory.|Infine, l'assembly può anche essere inserito nel **PublicAssemblies** sottodirectory. Gli assembly che si trovano **PublicAssemblies** vengono automaticamente rilevati e vengono visualizzate anche nel **aggiungere i riferimenti** nella finestra di dialogo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].<br /><br /> Gli assembly VSPackage devono essere posizionati solo nel **PublicAssemblies** directory se contengono i componenti destinati a essere riutilizzato da altri sviluppatori VSPackage gestiti. La maggior parte degli assembly non soddisfano questo criterio.|  
  
> [!NOTE]
>  Usare gli assembly con nome sicuro, con segno per tutti gli assembly dipendenti. Questi assembly devono anche essere installati nella global assembly cache (GAC) o la propria directory. Ciò consente di evitare conflitti con gli assembly con lo stesso nome di file di base, noto come associazione di "Weak"-name.

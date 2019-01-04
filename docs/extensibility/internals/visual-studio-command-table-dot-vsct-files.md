---
title: Visual Studio Command Table (. File Vsct) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 05c154a7ba87101f4a747b58d1a9ae4de16b7062
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988871"
---
# <a name="visual-studio-command-table-vsct-files"></a>File Visual Studio Command Table (con estensione vsct)
Un file di configurazione di tabella comandi è un file di testo che descrive il set di comandi che contiene un pacchetto VSPackage. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando compilatore tabella (VSCT) compila i file di configurazione basato su XML (file con estensione vsct) in file di output (con estensione CTO) tabella comando binary. I file con estensione CTO risultanti sono identici a quelli che vengono creati tramite il compilatore di tabella (CTC) comandi per compilare i file di configurazione con estensione CTC. Tuttavia, i file con estensione vsct basato su XML presenta alcuni vantaggi, ad esempio un editor XML e XML IntelliSense.  
  
 Per altre informazioni sulla sintassi e semantica dei file con estensione vsct, vedere [Progettazione tabella comandi XML (. File Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>In questa sezione  
 [Progettazione di file (con estensione vsct) della tabella di comandi XML](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Descrive come progettare i file con estensione vsct.  
  
 [Procedura: Creare una. File Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Confronta i metodi per la creazione di un file con estensione vsct. Descrive il processo per la creazione manuale di un nuovo file con estensione vsct.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Fornisce informazioni dettagliate su ogni sezione del file di configurazione XML di tabella comandi.  
  
 [Command Table Configuration (. File CTC)](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Viene presentata una panoramica del formato di file con estensione CTC deprecate.  
  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Descrive la specifica di formato di tabella comandi.  
  
 [Risorse nei pacchetti VSPackage](../../extensibility/internals/resources-in-vspackages.md)  
 Viene descritto come usare le risorse gestite e nei pacchetti VSPackage gestiti.  
  
 [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.
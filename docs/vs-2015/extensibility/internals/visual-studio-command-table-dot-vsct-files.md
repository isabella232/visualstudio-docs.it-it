---
title: Visual Studio Command Table (. File Vsct) | Microsoft Docs
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
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0692f0b32544edf7d5d7cec4b0ab4592c4219b3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530744"
---
# <a name="visual-studio-command-table-vsct-files"></a>File Visual Studio Command Table (con estensione vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Visual Studio Command Table (. File Vsct)](https://docs.microsoft.com/visualstudio/extensibility/internals/visual-studio-command-table-dot-vsct-files).  
  
Un file di configurazione di tabella comandi è un file di testo che descrive il set di comandi che contiene un pacchetto VSPackage. Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] comando compilatore tabella (VSCT) compila i file di configurazione basato su XML (file con estensione vsct) in file di output (con estensione CTO) tabella comando binary. I file con estensione CTO risultanti sono identici a quelli che vengono creati tramite il compilatore di tabella (CTC) comandi per compilare i file di configurazione con estensione CTC. Tuttavia, i file con estensione vsct basato su XML presenta alcuni vantaggi, ad esempio un editor XML e XML IntelliSense.  
  
 Per altre informazioni sulla sintassi e semantica dei file con estensione vsct, vedere [Progettazione tabella comandi XML (. File Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>In questa sezione  
 [Progettazione di file (con estensione vsct) della tabella di comandi XML](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Descrive come progettare i file con estensione vsct.  
  
 [Procedura: Creare un file con estensione vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Confronta i metodi per la creazione di un file con estensione vsct. Descrive il processo per la creazione manuale di un nuovo file con estensione vsct.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Fornisce informazioni dettagliate su ogni sezione del file di configurazione XML di tabella comandi.  
  
 [Command Table Configuration (. File CTC)](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Viene presentata una panoramica del formato di file con estensione CTC deprecate.  
  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Descrive la specifica di formato di tabella comandi.  
  
 [Risorse nei pacchetti VSPackage](../../extensibility/internals/resources-in-vspackages.md)  
 Viene descritto come usare le risorse gestite e nei pacchetti VSPackage gestiti.  
  
 [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.


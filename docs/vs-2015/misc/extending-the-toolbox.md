---
title: Estensione della casella degli strumenti | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: douge
ms.openlocfilehash: 674b9d1dcebc7ec4a9019c652f0909904fe952c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519515"
---
# <a name="extending-the-toolbox"></a>Estensione della casella degli strumenti
Il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **casella degli strumenti** fornisce una raccolta di oggetti che offrono funzionalità agli editor e ai designer tramite il meccanismo di trascinamento e rilascio dell'IDE.  
  
 Esistono due modi principali in cui un VSPackage funziona con il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **casella degli strumenti**:  
  
-   Un VSPackage può aggiungere nuovi elementi di dati e i controlli alla **casella degli strumenti**.  
  
-   Un VSPackage può essere una destinazione o un utente della funzionalità di **casella degli strumenti** esistente, supportando le operazioni di trascinamento della selezione e configurando l'aspetto della **casella degli strumenti**.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: Creare un controllo della casella degli strumenti che usa Windows Form](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Descrive come creare un controllo della casella degli strumenti usando il modello Controllo della casella degli strumenti Windows Forms.  
  
 [Creazione di un controllo della casella degli strumenti WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 Descrive come creare un controllo della casella degli strumenti usando il modello Controllo della casella degli strumenti WPF.  
  
 [Gestione della casella degli strumenti](../misc/managing-the-toolbox.md)  
 Descrive in che modo un pacchetto VSPackage può gestire il contenuto e l'aspetto della **casella degli strumenti**.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Procedura: gestire la finestra Casella degli strumenti](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Viene descritto come lavorare con i **casella degli strumenti** nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE).  
  
 [Procedura: Control the Toolbox](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Descrive come gestire la **casella degli strumenti** usando il modello di programmazione di automazione.  
  
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Viene illustrato come utilizzare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per creare elementi dell'interfaccia utente che corrispondono al resto dei servizi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].
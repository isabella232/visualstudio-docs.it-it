---
title: Estensione della casella degli strumenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: jillfra
ms.openlocfilehash: a1cf66baf73fe4a04dcb21b0c7ac7609214bea20
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967604"
---
# <a name="extending-the-toolbox"></a>Estensione della casella degli strumenti
La [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **di** fornisce una raccolta di oggetti che offrono funzionalità agli editor e ai designer tramite il meccanismo di trascinamento della selezione dell'IDE.  
  
 Esistono due modalità di base in cui un VSPackage funziona con la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **di**:  
  
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
 [Procedura: Gestire la finestra Casella degli strumenti](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Descrive come usare la **casella degli strumenti** nell'IDE (Integrated Development Environment) di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Procedura: Controllo della casella degli strumenti](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Descrive come gestire la **casella degli strumenti** usando il modello di programmazione di automazione.  
  
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Spiega come usare i servizi di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].
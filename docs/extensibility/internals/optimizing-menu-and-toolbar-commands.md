---
title: Ottimizzazione dei comandi di menu e barre degli strumenti | Microsoft Docs
description: Informazioni su come Visual Studio è in grado di ridurre al minimo la confusione dei comandi causata dall'aggiunta di VSPackage e dai comandi corrispondenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c7d289f9dadf7b3442f937c5b50cf038c802516
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063058"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Ottimizzazione dei comandi di menu e barre degli strumenti
L'aggiunta dei pacchetti VSPackage e dei comandi corrispondenti a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] può causare un'interfaccia utente affollata. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce modi per ridurre al minimo la confusione del comando dell'interfaccia utente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Miglioramento della disponibilità dei comandi](../../extensibility/internals/making-commands-available.md)

 Vengono fornite linee guida generali per ridurre al minimo il crowding dell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente quando si aggiungono i pacchetti VSPackage.

- [Linee guida per il posizionamento](../../extensibility/internals/command-placement-guidelines.md)

 Fornisce linee guida specifiche per l'implementazione di un pacchetto VSPackage in base alle dimensioni del set di comandi.

## <a name="related-sections"></a>Sezioni correlate
- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.

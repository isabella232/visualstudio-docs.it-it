---
title: Ottimizzazione dei comandi di menu e barra degli strumenti | Microsoft Docs
description: Informazioni su Visual Studio possibile ridurre al minimo la confusione dei comandi causata dall'aggiunta di VSPackage e dei comandi corrispondenti.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d95fd16a9d2582018313a47bea214e1788acd67c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102584"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Ottimizzazione dei comandi di menu e barre degli strumenti
L'aggiunta di VSPackage e dei comandi corrispondenti a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] può causare un'interfaccia utente piena. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce modi per ridurre al minimo la confusione dei comandi dell'interfaccia utente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Miglioramento della disponibilità dei comandi](../../extensibility/internals/making-commands-available.md)

 Fornisce linee guida generali per ridurre al minimo l'affollamento dell'interfaccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente quando si aggiungono VSPackage.

- [Linee guida per il posizionamento](../../extensibility/internals/command-placement-guidelines.md)

 Fornisce linee guida specifiche per l'implementazione di un pacchetto VSPackage in base alle dimensioni del set di comandi.

## <a name="related-sections"></a>Sezioni correlate
- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.

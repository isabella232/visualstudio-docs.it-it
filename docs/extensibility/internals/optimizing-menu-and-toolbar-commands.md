---
title: Ottimizzazione dei comandi di menu e barra degli strumenti | Microsoft Docs
description: Informazioni su Visual Studio ridurre al minimo la confusione dei comandi causata dall'aggiunta di VSPackage e dei comandi corrispondenti.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709543"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Ottimizzazione dei comandi di menu e barre degli strumenti
L'aggiunta di pacchetti VSPackage e dei comandi corrispondenti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a può causare un'interfaccia utente piena. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offre modi per ridurre al minimo la confusione dei comandi dell'interfaccia utente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Miglioramento della disponibilità dei comandi](../../extensibility/internals/making-commands-available.md)

 Fornisce linee guida generali per ridurre al minimo il crowding [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente quando si aggiungono pacchetti VSPackage.

- [Linee guida per il posizionamento](../../extensibility/internals/command-placement-guidelines.md)

 Fornisce linee guida specifiche per l'implementazione di un pacchetto VSPackage in base alle dimensioni del set di comandi.

## <a name="related-sections"></a>Sezioni correlate
- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.

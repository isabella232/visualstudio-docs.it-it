---
title: Routing di comandi in pacchetti VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5a5f884873e714c12708780a0e52f5f5574727fb
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512935"
---
# <a name="command-routing-in-vspackages"></a>Routing dei comandi nei pacchetti VSPackage
Un comando viene instradato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] basato sul contesto in cui viene eseguita. Viene indirizzato dal contesto iniziale verso l'esterno al contesto globale.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Algoritmo di routing di comandi](../../extensibility/internals/command-routing-algorithm.md)  
 Descrive l'ordine della risoluzione di routing dei comandi.  
  
 [Disponibilità dei comandi](../../extensibility/internals/command-availability.md)  
 Viene illustrato il routing di comandi.  
  
 [I comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Vengono fornite informazioni sul routing di comandi tra codice gestito e COM.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Oggetti di contesto di selezione](../../extensibility/internals/selection-context-objects.md)  
 Viene illustrato il modello per come è possibile determinare lo stato attivo contesto di selezione dell'utente in una finestra.  
  
 [I comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.
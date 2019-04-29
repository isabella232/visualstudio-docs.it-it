---
title: Comando, gruppo e il posizionamento della barra degli strumenti predefiniti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e84ca70383facc608740cd42a29c4ee769adb069
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909900"
---
# <a name="default-command-group-and-toolbar-placement"></a>Posizione di comando, il gruppo e sulla barra degli strumenti predefinita
Per prodotto uniformità e stabilità, l'interfaccia utente visualizza determinati gruppi di comandi per impostazione predefinita, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] includono le definizioni dei comandi e i gruppi di comandi. I VSPackage possono anche usare i comandi standard e i gruppi di comandi.

 I gruppi di comandi predefiniti possono essere suddivise in tre categorie: Comandi dell'IDE, comandi di prodotto e i comandi dell'editor.

## <a name="default-ide-commands"></a>Comandi predefiniti dell'IDE
 La barra degli strumenti dell'IDE predefinito include i comandi condivisi da tutti i prodotti contenuti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Sono inclusi i comandi relativi alle operazioni del progetto generico, ad esempio la **salvare** comando e il **Aggiungi elemento** comando. I pacchetti VSPackage devono non aggiungere o sottrarre da questa barra degli strumenti, con una sola eccezione: Se il prodotto o un pacchetto VSPackage aggiunge una nuova finestra degli strumenti, quindi la finestra deve essere aggiunto all'elenco di finestre degli strumenti disponibili nel **vista** menu. Nuovi prodotti o i pacchetti VSPackage possono aggiungere i propri sulla barra degli strumenti.

## <a name="default-product-commands"></a>Comandi predefinito del prodotto
 Ogni prodotto può fornire l'IDE con la propria barra degli strumenti predefinita che contiene importanti e comandi utilizzati di frequente. È consigliabile, tuttavia, per utilizzare i menu e barre degli strumenti ogni volta che è possibile esistenti e integrare con altre barre degli strumenti attività specifiche in base alle esigenze.

 Il campo priorità per una barra degli strumenti determina la posizione di riga. Zero priorità posiziona la barra degli strumenti nella terza riga (riga 3), sotto la barra dei menu (1 riga) e il **Standard** (riga 2) sulla barra degli strumenti. Pertanto, altre barre degli strumenti vengono visualizzati in corrispondenza di riga (priorità + 3). Le barre degli strumenti successive vengono inseriti nella stessa riga, se c'è spazio; in caso contrario, queste vengono spostate automaticamente la riga successiva.

## <a name="default-editor-commands"></a>Comandi dell'editor predefinito
 Un pacchetto VSPackage che fornisce un editor personalizzato deve fornire una barra degli strumenti predefinita che contiene i più importanti e comandi utilizzati di frequente in tale editor. Barra degli strumenti editor dovrebbe essere visualizzato quando l'editor è attivo e deve essere nascosto quando l'editor non è attivo. Tale visibilità viene controllata nel `VisibilityConstraints` elemento del *vsct* file.

 Barre degli strumenti Editor devono essere posizionati sotto le barre degli strumenti dell'IDE e il prodotto.

## <a name="see-also"></a>Vedere anche
- [I gruppi, menu e comandi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
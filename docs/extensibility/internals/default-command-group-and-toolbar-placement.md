---
title: Posizionamento di default Comando, Gruppo e Barra degli strumenti . Documenti Microsoft
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708895"
---
# <a name="default-command-group-and-toolbar-placement"></a>Posizionamento predefinito di comandi, gruppi e barre degli strumenti
Per uniformità e stabilità del prodotto, l'interfaccia utente visualizza determinati gruppi di comandi per impostazione predefinita e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce le definizioni per i comandi e i gruppi di comandi. VSPackage possono anche utilizzare i comandi standard e gruppi di comandi.

 I gruppi di comandi predefiniti rientrano in tre categorie: comandi IDE, comandi di prodotto e comandi dell'editor.

## <a name="default-ide-commands"></a>Comandi IDE predefiniti
 La barra degli strumenti predefinita dell'IDE include i comandi condivisi da tutti i prodotti contenuti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Questi includono comandi relativi alle operazioni di progetto generiche, ad esempio il **Salva** comando e il **Aggiungi elemento** comando. VSPackage non devono aggiungere o sottrarre da questa barra degli strumenti, con un'eccezione: se il prodotto o VSPackage aggiunge una nuova finestra degli strumenti, quindi la finestra deve essere aggiunto all'elenco delle finestre degli strumenti disponibili nel **visualizza** menu. Nuovi prodotti o VSPackage possono aggiungere la propria barra degli strumenti.

## <a name="default-product-commands"></a>Comandi di prodotto predefiniti
 Ogni prodotto può fornire l'IDE con la propria barra degli strumenti predefinita che contiene i comandi importanti e utilizzati di frequente. È meglio, tuttavia, utilizzare i menu e le barre degli strumenti esistenti quando possibile e integrarli con altre barre degli strumenti specifiche dell'attività in base alle esigenze.

 Il campo priorità per una barra degli strumenti ne determina la posizione delle righe. La priorità zero posiziona la barra degli strumenti sulla terza riga (riga 3), sotto la barra dei menu (riga 1) e la barra degli strumenti **Standard** (riga 2). Di conseguenza, le altre barre degli strumenti vengono visualizzate in corrispondenza della riga (priorità n. 3). Le barre degli strumenti successive vengono posizionate sulla stessa riga, se c'è spazio; in caso contrario, vengono spostati automaticamente alla riga successiva.

## <a name="default-editor-commands"></a>Comandi editor predefiniti
 Un pacchetto VSPackage che fornisce un editor personalizzato deve fornire una barra degli strumenti predefinita che contiene i comandi più importanti e utilizzati di frequente in tale editor. La barra degli strumenti dell'editor dovrebbe essere visualizzata quando l'editor è attivo e deve essere nascosta quando l'editor non è attivo. Questa visibilità è `VisibilityConstraints` controllata nell'elemento del file *vsct.*

 Le barre degli strumenti dell'editor devono essere posizionate sotto idE e le barre degli strumenti del prodotto.

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e gruppi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

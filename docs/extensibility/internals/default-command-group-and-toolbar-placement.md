---
title: Comandi, gruppi e posizionamento predefiniti della barra degli strumenti | Microsoft Docs
description: Informazioni sui comandi IDE, i comandi del prodotto e i comandi dell'editor, visualizzati per impostazione Visual Studio'interfaccia utente.
ms.custom: SEO-VS-2020
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 86b58d33f07eaae8ef93ddb82a77516a6eb182c467d77cc5857336bab6756844
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359611"
---
# <a name="default-command-group-and-toolbar-placement"></a>Posizionamento predefinito di comandi, gruppi e barre degli strumenti
Per l'uniformità e la stabilità del prodotto, l'interfaccia utente visualizza determinati gruppi di comandi per impostazione predefinita e fornisce le definizioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per i comandi e i gruppi di comandi. I pacchetti VSPackage possono anche usare i comandi standard e i gruppi di comandi.

 I gruppi di comandi predefiniti rientrano in tre categorie: comandi IDE, comandi del prodotto e comandi dell'editor.

## <a name="default-ide-commands"></a>Comandi IDE predefiniti
 La barra degli strumenti IDE predefinita include i comandi condivisi da tutti i prodotti contenuti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Sono inclusi i comandi relativi alle operazioni di progetto generiche, ad esempio il **comando Salva** e il **comando Aggiungi** elemento. I pacchetti VSPackage non devono essere aggiunti o sottratti da questa barra degli strumenti, con una sola eccezione: se il prodotto o vsPackage aggiunge una nuova finestra degli strumenti, la finestra deve essere aggiunta all'elenco di finestre degli strumenti disponibili nel **menu** Visualizza. Nuovi prodotti o VSPackage possono aggiungere la propria barra degli strumenti.

## <a name="default-product-commands"></a>Comandi del prodotto predefiniti
 Ogni prodotto può fornire all'IDE la propria barra degli strumenti predefinita che contiene comandi importanti e usati di frequente. È tuttavia meglio usare i menu e le barre degli strumenti esistenti quando possibile e integrarli con altre barre degli strumenti specifiche delle attività in base alle esigenze.

 Il campo di priorità per una barra degli strumenti ne determina la posizione delle righe. La priorità zero posiziona la barra degli strumenti sulla terza riga (riga 3), sotto la barra dei menu (riga 1) e sulla barra degli strumenti **Standard** (riga 2). Pertanto, altre barre degli strumenti vengono visualizzate in corrispondenza della riga (priorità + 3). Le barre degli strumenti successive vengono posizionate sulla stessa riga, se c'è spazio; In caso contrario, vengono spostati automaticamente nella riga successiva.

## <a name="default-editor-commands"></a>Comandi predefiniti dell'editor
 Un VSPackage che fornisce un editor personalizzato deve fornire una barra degli strumenti predefinita che contiene i comandi più importanti e usati di frequente in tale editor. La barra degli strumenti dell'editor dovrebbe essere visualizzata quando l'editor è attivo e deve essere nascosto quando l'editor non è attivo. Questa visibilità è controllata `VisibilityConstraints` nell'elemento del file *con estensione vsct.*

 Le barre degli strumenti dell'editor devono essere posizionate sotto le barre degli strumenti dell'IDE e del prodotto.

## <a name="see-also"></a>Vedi anche
- [Comandi, menu e gruppi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

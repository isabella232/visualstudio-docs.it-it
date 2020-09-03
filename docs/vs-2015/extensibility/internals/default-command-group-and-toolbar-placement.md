---
title: Posizionamento predefinito di comandi, gruppi e barre degli strumenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7fc877332f7db7b27c4a30c23f1ac395a4fc22e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196886"
---
# <a name="default-command-group-and-toolbar-placement"></a>Posizionamento predefinito di comandi, gruppi e barre degli strumenti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per uniformità e stabilità del prodotto, l'interfaccia utente visualizza determinati gruppi di comandi per impostazione predefinita e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce le definizioni per i comandi e i gruppi di comandi. I pacchetti VSPackage possono anche usare i comandi e i gruppi di comandi standard.  
  
 I gruppi di comandi predefiniti rientrano in tre categorie: comandi dell'IDE, comandi del prodotto e comandi dell'editor.  
  
## <a name="default-ide-commands"></a>Comandi IDE predefiniti  
 La barra degli strumenti dell'IDE predefinita include i comandi condivisi da tutti i prodotti contenuti in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Sono inclusi i comandi correlati a operazioni di progetto generiche, ad esempio il comando **Salva** e il comando **Aggiungi elemento** . I pacchetti VSPackage non devono essere aggiunti o sottratti dalla barra degli strumenti, con un'eccezione: se il prodotto o il pacchetto VSPackage aggiunge una nuova finestra degli strumenti, la finestra deve essere aggiunta all'elenco delle finestre degli strumenti disponibili dal menu **Visualizza** . Nuovi prodotti o VSPackage possono aggiungere la propria barra degli strumenti.  
  
## <a name="default-product-commands"></a>Comandi del prodotto predefiniti  
 Ogni prodotto può fornire l'IDE con la propria barra degli strumenti predefinita che contiene i comandi importanti e usati di frequente. Tuttavia, è preferibile utilizzare i menu e le barre degli strumenti esistenti laddove possibile e integrarli con altre barre degli strumenti specifiche dell'attività in base alle esigenze.  
  
 Il campo relativo alla priorità per una barra degli strumenti determina la posizione delle righe. Zero Priority posiziona la barra degli strumenti sulla terza riga (riga 3), sotto la barra dei menu (riga 1) e la barra degli strumenti **standard** (riga 2). Quindi, altre barre degli strumenti vengono visualizzate alla riga (priorità + 3). Le barre degli strumenti successive vengono posizionate nella stessa riga, se è presente spazio; in caso contrario, vengono spostati automaticamente nella riga successiva.  
  
## <a name="default-editor-commands"></a>Comandi dell'editor predefinito  
 Un pacchetto VSPackage che fornisce un editor personalizzato deve fornire una barra degli strumenti predefinita che contiene i comandi più importanti e usati di frequente in tale editor. La barra degli strumenti dell'editor deve essere visualizzata quando l'editor è attivo e deve essere nascosto quando l'editor non è attivo. Questa visibilità viene controllata nell'oggetto `VisibilityConstraints Element` del file con estensione vsct.  
  
 Le barre degli strumenti dell'editor devono essere posizionate sotto la barra degli strumenti dell'IDE e del prodotto.  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi, menu e gruppi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

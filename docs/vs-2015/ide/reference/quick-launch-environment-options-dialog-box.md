---
title: Avvio veloce, Ambiente, finestra di dialogo Opzioni | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bf2e22db54e064de6716d4ca1325a9e5435318f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517581"
---
# <a name="quick-launch-environment-options-dialog-box"></a>Avvio veloce, Ambiente, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [avvio veloce, ambiente, finestra di dialogo Opzioni](https://docs.microsoft.com/visualstudio/ide/reference/quick-launch-environment-options-dialog-box).  
  
  
È possibile usare **Avvio veloce** per effettuare una rapida ricerca ed eseguire le azioni delle risorse IDE, ad esempio opzioni, modelli, menu. Non è possibile usare **Avvio veloce** per cercare codice e simboli. La casella di ricerca **Avvio veloce** si trova nell'angolo superiore destro della barra dei menu ed è possibile accedervi premendo CTRL+Q. È sufficiente immettere la stringa di ricerca nella casella. Per cercare stringhe contenenti @, usare ‘@@’.   
  
 **Avvio veloce** è abilitato per impostazione predefinita quando si installa Visual Studio. Nella barra dei menu è possibile mostrare o nascondere **Avvio veloce** scegliendo **Strumenti**, **Opzioni**. Espandere il nodo **Ambienti** e quindi scegliere **Avvio veloce**. Selezionare o deselezionare la casella di controllo **Abilita avvio veloce**. In questa pagina è anche possibile abilitare o disabilitare le categorie di ricerca.  
  
## <a name="category-list"></a>Elenco di categorie  
 I risultati delle ricerche effettuate in Avvio veloce vengono visualizzati in quattro categorie: **Usati di recente**, **Menu**, **Opzioni** e **Documenti aperti** con un'indicazione del numero di elementi in ogni categoria. Per scorrere i risultati della ricerca per categoria, premere CTRL+Q per mostrare tutti i risultati della categoria successiva. Dopo che viene visualizzata l'ultima categoria, premendo CTRL+Q è possibile visualizzare alcuni risultati di ogni categoria. È possibile usare CTRL+MAIUSC+Q per spostarsi tra le categorie in ordine inverso. Per visualizzare tutti i risultati della ricerca in una categoria, scegliere il nome della categoria.  
  
 È possibile usare i metodi rapidi seguenti per limitare la ricerca a categorie specifiche.  
  
|Category|Metodo rapido|Descrizione metodo rapido|  
|--------------|--------------|--------------------------|  
|Usati di recente|@mru<br /><br /> Ad esempio, `@mru font`.|Visualizza fino a cinque elementi **Usati di recente**.|  
|Menu|@menu<br /><br /> Ad esempio, `@menu font`.|Limita la ricerca alle voci di menu.|  
|Opzioni|@opt<br /><br /> Ad esempio, `@opt font`.|Limita la ricerca alle impostazioni nella finestra di dialogo **Opzioni**.|  
|Documenti|@doc<br /><br /> Ad esempio, `@doc font`.|Limita la ricerca ai percorsi e ai nomi di file dei documenti aperti per i criteri di ricerca, ma non esegue la ricerca nel testo all'interno dei file.|  
  
> [!NOTE]
>  È possibile modificare le combinazioni di tasti nella pagina **Generale**, **Tastiera** della finestra di dialogo **Opzioni**.  
  
## <a name="show-previous-results"></a>Visualizzare i risultati precedenti  
 Per impostazione predefinita, il termine di ricerca immesso non viene mantenuto tra sessioni di ricerca. Se si cerca un termine, si sposta il cursore all'esterno dell'area **Avvio veloce** e quindi si torna nell'area, la stringa di ricerca viene cancellata. Per mantenere i risultati della ricerca, nella finestra di dialogo **Opzioni** scegliere **Avvio veloce** e quindi selezionare la casella di controllo **Mostra risultati della ricerca precedente quando viene attivato Avvio veloce** . In seguito, se si esegue una ricerca, si esce dall'area Avvio veloce e si torna nell'aera, verrà mantenuto il termine di ricerca usato per ultimo e verranno inoltre visualizzati i risultati della ricerca.  
  
 Per i suggerimenti e i consigli più recenti sull'uso di **Avvio veloce**, vedere il [blog di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=236054).  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi generali dell'interfaccia utente (Visual Studio)](../../ide/reference/general-user-interface-elements-visual-studio.md)   
 [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)



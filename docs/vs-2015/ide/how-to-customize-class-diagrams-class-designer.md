---
title: 'Procedura: Personalizzare i diagrammi classi (Progettazione classi) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a4b163aef25972968933d3352486aab9ebbf962
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950976"
---
# <a name="how-to-customize-class-diagrams-class-designer"></a>Procedura: personalizzare i diagrammi classi (Progettazione classi)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare la modalità con cui i diagrammi classi visualizzano le informazioni. È possibile personalizzare l'intero diagramma o i singoli tipi nell'area di progettazione.  
  
 È possibile, ad esempio, regolare il livello di zoom di un intero diagramma classi, modificare il modo in cui singoli membri di tipo vengono raggruppati e ordinati, nascondere o visualizzare relazioni e spostare singoli tipi o set di tipi in qualsiasi punto del diagramma.  
  
> [!NOTE]
>  La personalizzazione della modalità di visualizzazione delle forme nel diagramma non modifica il codice sottostante per i tipi rappresentati nel diagramma.  
  
 Le sezioni contenenti membri di tipo, ad esempio la sezione Proprietà in una classe, vengono definite raggruppamenti. È possibile nascondere o visualizzare singoli raggruppamenti e membri di tipo.  
  
 **In questo argomento**  
  
-   [Eseguire lo zoom avanti e indietro sul diagramma classi](../ide/how-to-customize-class-diagrams-class-designer.md#ZoomInOut)  
  
-   [Personalizzare il raggruppamento e l'ordinamento dei membri di tipo](../ide/how-to-customize-class-diagrams-class-designer.md#CustomizeGroupingSorting)  
  
-   [Nascondere i raggruppamenti in un tipo](../ide/how-to-customize-class-diagrams-class-designer.md#HideCompartments)  
  
-   [Nascondere singoli membri in un tipo](../ide/how-to-customize-class-diagrams-class-designer.md#HideMembers)  
  
-   [Mostrare raggruppamenti e membri nascosti in un tipo](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayHiddenCompartmentsAndMemberrs)  
  
-   [Nascondere relazioni](../ide/how-to-customize-class-diagrams-class-designer.md#HideAssociationAndInheritance)  
  
-   [Mostrare relazioni nascoste](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayAssociationAndInheritance)  
  
-   [Rimuovere una forma da un diagramma di classi](../ide/how-to-customize-class-diagrams-class-designer.md#RemoveCodeAndShape)  
  
-   [Eliminare una forma di tipo e il codice sottostante](../ide/how-to-customize-class-diagrams-class-designer.md#DeleteTypeShapeAndCode)  
  
##  <a name="ZoomInOut"></a> Eseguire lo zoom avanti e indietro sul diagramma classi  
  
1.  Aprire e selezionare un file di diagramma classi in Progettazione classi.  
  
2.  Nella barra degli strumenti di Progettazione classi fare clic sul pulsante **Zoom avanti** o **Zoom indietro** per modificare il livello di zoom dell'area di progettazione.  
  
     oppure  
  
     Specificare un particolare valore di zoom. È possibile usare l'elenco a discesa **Zoom** o digitare un livello di zoom valido (l'intervallo valido è compreso tra 10% e 400%).  
  
    > [!NOTE]
    >  La modifica del livello di zoom non influisce sulla scala dello stampato del diagramma classi.  
  
##  <a name="CustomizeGroupingSorting"></a> Personalizzare il raggruppamento e l'ordinamento dei membri di tipo  
  
1.  Aprire e selezionare un file di diagramma classi in Progettazione classi.  
  
2.  Fare clic con il pulsante destro del mouse in un punto vuoto dell'area di progettazione e scegliere **Raggruppa membri**.  
  
3.  Selezionare una delle opzioni disponibili:  
  
    1.  **Raggruppa per tipo** separa i singoli membri di tipo in un elenco raggruppato di proprietà, metodi, eventi e campi. I singoli gruppi dipendono dalla definizione delle entità: ad esempio, una classe non visualizzerà alcun gruppo di eventi se non esistono ancora eventi definiti per tale classe.  
  
    2.  **Raggruppa per accesso** separa i singoli membri di tipo in un elenco raggruppato basato sui modificatori di accesso del membro. Ad esempio, Public e Private.  
  
    3.  **Ordina alfabeticamente** visualizza gli elementi che costituiscono un'entità come singolo elenco in ordine alfabetico. L'elenco è ordinato in ordine crescente.  
  
##  <a name="HideCompartments"></a> Nascondere i raggruppamenti in un tipo  
  
1.  Aprire e selezionare un file di diagramma classi in Progettazione classi.  
  
2.  Fare clic con il pulsante destro del mouse sulla categoria del membro nel tipo da personalizzare (ad esempio, selezionare il nodo **Metodi** in una classe).  
  
3.  Fare clic su **Nascondi raggruppamento**.  
  
     Il raggruppamento selezionato verrà rimosso dal contenitore del tipo.  
  
##  <a name="HideMembers"></a> Nascondere singoli membri in un tipo  
  
1.  Aprire e selezionare un file di diagramma classi in Progettazione classi.  
  
2.  Fare clic con il pulsante destro del mouse sul membro nel tipo da nascondere.  
  
3.  Fare clic su **Nascondi**.  
  
     Il membro selezionato verrà rimosso dal contenitore del tipo.  
  
##  <a name="DisplayHiddenCompartmentsAndMemberrs"></a> Mostrare raggruppamenti e membri nascosti in un tipo  
  
1.  Aprire e selezionare un file di diagramma classi in Progettazione classi.  
  
2.  Fare clic con il pulsante destro del mouse sul nome del tipo con il raggruppamento nascosto.  
  
3.  Fare clic su **Mostra tutti i membri**.  
  
     Tutti i raggruppamenti e i membri nascosti verranno visualizzati nel contenitore del tipo.  
  
##  <a name="HideAssociationAndInheritance"></a> Nascondere relazioni  
  
1.  Aprire e selezionare un file di diagramma classi in Progettazione classi.  
  
2.  Fare clic con il pulsante destro del mouse sulla linea di associazione o ereditarietà che si desidera nascondere.  
  
3.  Fare clic su **Nascondi** per le linee di associazione e scegliere **Nascondi linea ereditarietà** per le linee di ereditarietà.  
  
4.  Fare clic su **Mostra tutti i membri**.  
  
     Tutti i raggruppamenti e i membri nascosti verranno visualizzati nel contenitore del tipo.  
  
##  <a name="DisplayAssociationAndInheritance"></a> Mostrare relazioni nascoste  
  
1. Aprire e selezionare un file di diagramma classi in Progettazione classi.  
  
2. Fare clic con il pulsante destro del mouse sul tipo con l'associazione o l'ereditarietà nascosta.  
  
   Fare clic su **Mostra tutti i membri** per le linee di associazione e su **Mostra classe base** o **Mostra classi derivate** per le linee di ereditarietà.  
  
##  <a name="RemoveCodeAndShape"></a> Rimuovere una forma da un diagramma di classi  
 È possibile rimuovere una forma di tipo dal diagramma di classi senza influire sul codice sottostante del tipo. La rimozione delle forme dei tipi da un diagramma classi influirà solo sul diagramma corrente: il codice sottostante che definisce il tipo e gli altri diagrammi in cui viene visualizzato il tipo non saranno interessati.  
  
1.  Nel diagramma classi selezionare la forma del tipo da rimuovere dal diagramma.  
  
2.  Scegliere **Rimuovi dal diagramma** dal menu **Modifica**.  
  
     La forma del tipo ed eventuali linee di associazione o ereditarietà connesse ad essa connesse non appariranno più sul diagramma.  
  
##  <a name="DeleteTypeShapeAndCode"></a> Eliminare una forma di tipo e il codice sottostante  
  
1.  Fare clic con il pulsante destro del mouse sulla forma nell'area di progettazione.  
  
2.  Scegliere **Elimina codice** dal menu di scelta rapida.  
  
     La forma verrà rimossa dal diagramma e il codice sottostante verrà eliminato dal progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Working with Class Diagrams (Class Designer)](../ide/working-with-class-diagrams-class-designer.md)  (Uso di diagrammi classi (Progettazione classi))  
 [Procedura: Passare dalla notazione membro alla notazione associazione (Progettazione classi)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)   
 [Procedura: Visualizzare i tipi esistenti (Progettazione classi)](../ide/how-to-view-existing-types-class-designer.md)   
 [Visualizzazione dei tipi e delle relazioni (Progettazione classi)](../ide/viewing-types-and-relationships-class-designer.md)




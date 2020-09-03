---
title: Finestra di dialogo schemi XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d637cb3c25772685d5a782eb74bf94878ded36c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669426"
---
# <a name="xml-schemas-dialog-box"></a>Finestra di dialogo Schemi XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La finestra di dialogo **schemi XML** consente di selezionare gli schemi XML Schema Definition Language (XSD) da associare a un documento XML. È possibile selezionare uno schema dalla cache degli schemi oppure specificare uno schema che non si trova nella cache. Gli schemi selezionati vengono considerati parte di un set di schemi, che viene usato per IntelliSense e per la convalida dei documenti XML.

 È possibile accedere alla finestra di dialogo **schemi XML** facendo clic sul pulsante **schemi** nella finestra proprietà del documento oppure selezionando **schemi** dal menu **XML** .

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **USA** Consente di selezionare la modalità di utilizzo dello schema XML.

- **Automatico**. Questo schema non è usato dal documento corrente ma è disponibile per l'associazione automatica. Se il documento XML dichiara uno spazio di nomi che corrisponde al `targetNamespace` di questo schema, lo schema viene automaticamente associato e incluso nel set di schemi.

- **Utilizzare questo schema**. Questo schema è usato dal documento corrente. L'utilizzo di questo schema è stato richiesto in modo esplicito selezionando questa colonna oppure lo schema è stato associato automaticamente in base a un `targetNamespace` corrispondente.

- Non **utilizzare gli schemi selezionati**. Questo schema non è usato dal documento corrente anche se dispone di un `targetNamespace` corrispondente. Questa impostazione può essere utile per la risoluzione di conflitti nel caso in cui la cache dello schema o la soluzione contengano più versioni dello stesso schema.

  **Spazio dei nomi di destinazione** Consente di visualizzare lo spazio dei nomi di destinazione associato a XML Schema.

  **Nome file** Consente di visualizzare il nome del file di XML Schema.

  **Aggiungi** Apre la finestra di dialogo **Apri schema XSD** , che consente di selezionare schemi aggiuntivi da aggiungere al set di schemi. Quando si aggiunge uno schema al set di schemi, il valore della colonna **use** è impostato in modo da **utilizzare questo schema**.

  **Rimuovi** Consente di rimuovere lo schema attualmente selezionato dal set di schemi. L'operazione rimuove lo schema dalla cache degli schemi in memoria, ma non dal file system.

## <a name="see-also"></a>Vedere anche
 [Componenti dell'editor XML](../xml-tools/xml-editor-components.md) [procedura: selezionare gli schemi XML per l'utilizzo](../xml-tools/how-to-select-the-xml-schemas-to-use.md) [della cache degli schemi](../xml-tools/schema-cache.md)

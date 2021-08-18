---
title: XML Schema
description: Informazioni sulla finestra di dialogo XML Schemas usata per selezionare gli schemi XSD (XML Schema Definition Language) da associare a un documento XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: ce4aee5707144abd086056f0022cc4aac44618db
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122579"
---
# <a name="xml-schemas-dialog-box"></a>Finestra di dialogo XML Schema

La finestra di dialogo XML **Schemas** consente di selezionare gli schemi XSD (XML Schema Definition Language) da associare a un documento XML. È possibile selezionare uno schema dalla cache degli schemi oppure specificare uno schema che non si trova nella cache. Gli schemi selezionati vengono considerati parte di un set di schemi, che viene usato per IntelliSense e per la convalida dei documenti XML.

È possibile accedere alla finestra di dialogo **XML Schemas** facendo clic sul pulsante **Schemi** nella finestra delle proprietà del documento oppure selezionando **Schemi** dal menu **XML.**

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**Uso**

Consente di selezionare la modalità di utilizzo di XML Schema.

- **Automatico** Questo schema non è usato dal documento corrente ma è disponibile per l'associazione automatica. Se il documento XML dichiara uno spazio di nomi che corrisponde al `targetNamespace` di questo schema, lo schema viene automaticamente associato e incluso nel set di schemi.

- **Usare questo schema**. Questo schema è usato dal documento corrente. L'utilizzo di questo schema è stato richiesto in modo esplicito selezionando questa colonna oppure lo schema è stato associato automaticamente in base a un `targetNamespace` corrispondente.

- **Non usare schemi selezionati.** Questo schema non è usato dal documento corrente anche se dispone di un `targetNamespace` corrispondente. Questa impostazione può essere utile per la risoluzione di conflitti nel caso in cui la cache dello schema o la soluzione contengano più versioni dello stesso schema.

**Spazio dei nomi di destinazione**

Consente di visualizzare lo spazio dei nomi di destinazione associato allo schema XML.

**Nome file**

Consente di visualizzare il nome del file di XML Schema.

**Aggiungere**

Apre la **finestra di dialogo Apri schema XSD** che consente di selezionare schemi aggiuntivi da aggiungere al set di schemi. Quando si aggiunge uno schema al set di schemi, il **valore della** colonna Usa è impostato su Usa **questo schema**.

**Rimuovi**

Consente di rimuovere lo schema attualmente selezionato dal set di schemi. L'operazione rimuove lo schema dalla cache degli schemi in memoria, ma non dal file system.

## <a name="see-also"></a>Vedi anche

- [Procedura: Selezionare gli SCHEMI XML da usare](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Cache dello schema](../xml-tools/schema-cache.md)

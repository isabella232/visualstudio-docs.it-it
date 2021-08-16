---
title: 'Procedura: Aggiungere e rimuovere dipendenze di funzionalità | Microsoft Docs'
description: Vedere come aggiungere e rimuovere dipendenze di funzionalità alla soluzione SharePoint usando Progettazione funzionalità in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d0e2a1ad31543e9248502e822c3905e274887c463cba5fe4c63c0b4c4acbb5c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425297"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Procedura: Aggiungere e rimuovere dipendenze di funzionalità
  La SharePoint può dipendere da altre funzionalità per funzionalità o dati. In questi casi, è possibile contrassegnare queste altre funzionalità come dipendenze per la funzionalità. In questo modo, il server SharePoint verifica che le funzionalità dipendenti siano attivate prima dell'attivazione della funzionalità.

## <a name="add-dependencies"></a>Aggiungere le dipendenze
 È possibile aggiungere altre funzionalità nella soluzione come dipendenze. In questo modo, è possibile assicurarsi che le funzionalità necessarie siano installate e attivate prima dell'installazione della funzionalità.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Per aggiungere una dipendenza da una funzionalità nella soluzione

1. Aprire Progettazione funzionalità, espandere il **nodo Dipendenze attivazione funzionalità** e quindi scegliere il **pulsante** Aggiungi.

2. Nella finestra di dialogo Aggiungi dipendenze  attivazione funzionalità scegliere il pulsante di opzione Aggiungi una dipendenza dalle funzionalità nella soluzione, scegliere  il titolo della funzionalità che si vuole aggiungere come dipendenza e quindi scegliere il pulsante Aggiungi. 

     È possibile aggiungere più funzionalità scegliendo più titoli durante la scelta del **tasto CTRL.**

## <a name="addi-custom-dependencies"></a>Dipendenze personalizzate addi
 È possibile aggiungere funzionalità già distribuite in un server SharePoint come dipendenza. In questo modo, il SharePoint di attivazione verifica che tutte le funzionalità dipendenti siano attivate prima dell'installazione della funzionalità.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Per aggiungere una dipendenza in base all'ID funzionalità

1. Aprire Progettazione funzionalità, espandere il **nodo Dipendenze attivazione funzionalità** e quindi scegliere il **pulsante** Aggiungi.

2. Nella finestra **di dialogo Aggiungi dipendenze attivazione funzionalità** scegliere il pulsante di opzione Aggiungi **dipendenza** personalizzata.

3. Nella casella **di testo ID** funzionalità immettere il GUID per la funzionalità che si desidera contrassegnare come dipendenza di attivazione e quindi scegliere il **pulsante** Aggiungi.

## <a name="edit-custom-dependencies"></a>Modificare le dipendenze personalizzate
 È possibile modificare le dipendenze personalizzate aggiunte in precedenza. Tuttavia, le funzionalità dipendenti presenti nella soluzione possono essere rimosse solo e non modificate.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Per modificare una dipendenza da una funzionalità nella soluzione

1. Aprire Progettazione funzionalità e quindi espandere il **nodo Dipendenze attivazione** funzionalità.

2. Scegliere il nome della funzionalità da modificare e quindi scegliere **il pulsante** Modifica.

3. Nella finestra **di dialogo Modifica dipendenza attivazione** funzionalità personalizzata modificare il titolo, l'ID funzionalità o la descrizione, quindi scegliere il pulsante **Invia.**

## <a name="remove-dependencies"></a>Rimuovere le dipendenze

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Per rimuovere una dipendenza da una funzionalità nella soluzione

1. In Progettazione funzionalità espandere il nodo Dipendenze attivazione **funzionalità,** scegliere il nome della funzionalità da rimuovere e quindi scegliere **il pulsante** Rimuovi.

## <a name="see-also"></a>Vedi anche
- [Creare SharePoint funzionalità](../sharepoint/creating-sharepoint-features.md)
- [Procedura: Personalizzare una SharePoint personalizzata](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: Aggiungere e rimuovere elementi per SharePoint funzionalità](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)

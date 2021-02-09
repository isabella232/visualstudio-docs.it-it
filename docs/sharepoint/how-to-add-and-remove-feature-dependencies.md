---
title: 'Procedura: aggiungere e rimuovere dipendenze di funzionalità | Microsoft Docs'
description: Vedere come aggiungere e rimuovere dipendenze di funzionalità dalla soluzione SharePoint usando progettazione funzionalità in Visual Studio.
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
ms.workload:
- office
ms.openlocfilehash: ebec7f6b1f6d777ce7b3b914ac5c1d5629190fcc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923577"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Procedura: aggiungere e rimuovere dipendenze di funzionalità
  La funzionalità di SharePoint potrebbe dipendere da altre funzionalità per le funzionalità o i dati. In questi casi, è possibile contrassegnare le altre funzionalità come dipendenze per la funzionalità. In questo modo, il server SharePoint garantisce che le funzionalità dipendenti siano attivate prima che la funzionalità venga attivata.

## <a name="add-dependencies"></a>Aggiungere le dipendenze
 È possibile aggiungere altre funzionalità nella soluzione come dipendenze. In questo modo, è possibile assicurarsi che le funzionalità richieste siano installate e attivate prima di installare la funzionalità.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Per aggiungere una dipendenza da una funzionalità della soluzione

1. Aprire Progettazione funzionalità, espandere il nodo **dipendenze attivazione funzionalità** , quindi scegliere il pulsante **Aggiungi** .

2. Nella finestra di dialogo **Aggiungi dipendenze attivazione funzionalità** , scegliere il pulsante di opzione **Aggiungi dipendenza dalle funzionalità nel campo soluzione** , scegliere il titolo della funzionalità che si desidera aggiungere come dipendenza, quindi scegliere il pulsante **Aggiungi** .

     È possibile aggiungere più di una funzionalità scegliendo più titoli mentre si sceglie il tasto **CTRL** .

## <a name="addi-custom-dependencies"></a>Dipendenze personalizzate
 È possibile aggiungere funzionalità che sono già state distribuite in un server SharePoint come dipendenza. In questo modo, il processo di attivazione di SharePoint verifica che tutte le funzionalità dipendenti siano attivate prima di installare la funzionalità.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Per aggiungere una dipendenza in base all'ID funzionalità

1. Aprire Progettazione funzionalità, espandere il nodo **dipendenze attivazione funzionalità** , quindi scegliere il pulsante **Aggiungi** .

2. Nella finestra di dialogo **Aggiungi dipendenze attivazione funzionalità** scegliere il pulsante di opzione **Aggiungi dipendenza personalizzata** .

3. Nella casella di testo **ID funzionalità** immettere il GUID della funzionalità che si desidera contrassegnare come dipendenza di attivazione, quindi scegliere il pulsante **Aggiungi** .

## <a name="edit-custom-dependencies"></a>Modificare le dipendenze personalizzate
 È possibile modificare le dipendenze personalizzate aggiunte in precedenza. Tuttavia, le funzionalità dipendenti presenti nella soluzione possono essere rimosse solo, non modificate.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Per modificare una dipendenza da una funzionalità della soluzione

1. Aprire Progettazione funzionalità, quindi espandere il nodo **dipendenze di attivazione funzionalità** .

2. Scegliere il nome della funzionalità che si desidera modificare, quindi scegliere il pulsante **modifica** .

3. Nella finestra di dialogo **modifica dipendenza personalizzata attivazione funzionalità** modificare il titolo, l'ID funzionalità o la descrizione, quindi scegliere il pulsante **Invia** .

## <a name="remove-dependencies"></a>Rimuovi dipendenze

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Per rimuovere una dipendenza da una funzionalità della soluzione

1. In progettazione funzionalità espandere il nodo **dipendenze attivazione funzionalità** , scegliere il nome della funzionalità che si desidera rimuovere, quindi scegliere il pulsante **Rimuovi** .

## <a name="see-also"></a>Vedi anche
- [Creazione di funzionalità di SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Procedura: personalizzare una funzionalità di SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: aggiungere e rimuovere elementi nelle funzionalità di SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)

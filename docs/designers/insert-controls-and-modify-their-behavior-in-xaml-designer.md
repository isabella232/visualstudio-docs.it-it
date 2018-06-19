---
title: Inserire i controlli e modificarne il comportamento in XAML Designer
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: e2ec53e78bc88e18d9ba8e77aa888ffa855b64ea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924155"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Inserire i controlli e modificarne il comportamento in XAML Designer

I controlli consentono agli utenti di interagire con l'app. È possibile usarli per raccogliere informazioni e per eseguire azioni come animare un oggetto o eseguire query su un'origine dati.

## <a name="add-controls-to-the-artboard"></a>Aggiungere controlli alla tavola da disegno

È possibile trascinare controlli dal pannello **Asset** nella **tavola da disegno**e quindi modificarli nella finestra **Proprietà** .

![Controlli della scheda Asset di Blend](../designers/media/blend_assetsflipview_xaml.png)

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Creare un controllo da un'immagine, una forma o un percorso

È possibile trasformare qualsiasi oggetto in un controllo.

![Finestra di dialogo Crea controllo di Blend](../designers/media/blend_makeintocontrol_xaml.png)

Immaginare, ad esempio, l'immagine di un televisore al centro di una pagina. È possibile creare controlli da piccole immagini simili ai pulsanti del televisore per consentire agli utenti di cambiare canale facendo clic su questi pulsanti

che di fatto sono controlli. Grazie ai controlli è possibile rispondere alle interazioni dell'utente, in questo caso quando l'utente fa clic su un pulsante.

Per creare un controllo, selezionare un oggetto. Scegliere quindi **Crea controllo** dal menu **Strumenti**.

## <a name="make-controls-do-things"></a>Impostare i controlli per l'esecuzione di operazioni

I controlli possono eseguire azioni durante le interazioni degli utenti, ad esempio possono avviare un'animazione, aggiornare un'origine dati o riprodurre un video.

Per impostare i controlli per l'esecuzione di operazioni, usare *trigger*, *comportamenti*ed *eventi* .

### <a name="triggers"></a>trigger

Un *trigger* modifica una proprietà o esegue un'attività in risposta a un evento o a una modifica in un'altra proprietà. Ad esempio, è possibile modificare il colore di un pulsante al passaggio del mouse.

![Pannello "Trigger"](../designers/media/custom_button_blend_propertytriggerinfo.png)

### <a name="behaviors"></a>comportamenti

Un *comportamento* è un pacchetto di codice riutilizzabile che consente di eseguire altre operazioni oltre alla modifica delle proprietà, ad esempio di eseguire query su un servizio dati. Blend include una piccola raccolta di comportamenti, ma è possibile aggiungerne altri. Trascinare un comportamento su un oggetto qualsiasi nella tavola da disegno e quindi personalizzare il comportamento impostando le proprietà.

![FluidMoveBehavior nel pannello Proprietà](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

**Video:** ![Icona Riproduci](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Suggerimenti per Blend: Introduzione all'uso dei comportamenti, parte 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Eventi

Per la massima flessibilità è possibile gestire un *evento*. Sarà necessario scrivere codice.
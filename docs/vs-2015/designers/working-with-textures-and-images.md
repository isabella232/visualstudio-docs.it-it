---
title: Uso di trame e immagini | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 93813aa734c615e7f045c98c776e600be4ee3fab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663930"
---
# <a name="working-with-textures-and-images"></a>Uso di trame e immagini
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare l'editor di immagini in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per creare e modificare trame e immagini. L'editor di immagini supporta formati avanzati per trame e immagini, come quelli usati nello sviluppo di app DirectX.

> [!NOTE]
> L'editor di immagini non supporta immagini con livello di colore minimo, come icone e cursori. Per creare o modificare questi tipi di immagini, usare l' [Image Editor for Icons](https://msdn.microsoft.com/library/586d2b8b-0348-4883-a85d-1ff0ddbf14dd).

## <a name="textures-and-images"></a>Trame e immagini
 A un livello di base, le trame e le immagini sono semplicemente tabelle di dati usate per offrire dettagli visivi nelle app grafiche. Il tipo di dettagli offerti da una trama o un'immagine dipende dal modo in cui viene usata, ma i campioni di colore, i valori alfa (trasparenza), le normali alla superficie e i valori di altezza costituiscono alcuni esempi comuni. La differenza principale tra una trama e un'immagine è che una trama è destinata a essere usata insieme a una rappresentazione di forma, in genere un modello 3D, per esprimere una scena o un oggetto completo, mentre un'immagine è in genere una rappresentazione autonoma della scena o dell'oggetto.

 Ecco alcuni tra i tipi comuni di trame:

 Mappe di trama le mappe di trama contengono valori di colore organizzati come matrice a una, due o tre dimensioni. e vengono usate per fornire dettagli di colore sull'oggetto interessato. I colori usano in genere per la codifica i canali di colore RGB (Red, Green, Blue, rosso, verde e blu) e possono includere un quarto canale, chiamato alfa, che rappresenta la trasparenza. Meno frequentemente i colori usano un'altra combinazione colori per la codifica oppure il quarto canale può contenere dati diversi da alfa, ad esempio di altezza.

 Normal Maps le mappe normali contengono normali di superficie. e vengono usate per fornire dettagli di illuminazione sull'oggetto interessato. Le normali usano in genere la codifica con i componenti di colore rosso, verde e blu per archiviare le dimensioni x, y e z del vettore. Tuttavia, esistono altre codifiche, ad esempio quelle basate su coordinate polari.

 Le mappe Height Height maps contengono dati di campo Height. Queste mappe vengono usate per offrire una forma di dettagli geometrici sull'oggetto interessato, usando il codice dello shader per calcolare l'effetto desiderato o per fornire punti dati da usare, ad esempio, per la generazione di terreni. Per la codifica i valori di altezza usano in genere un solo canale in una trama.

 Le mappe Cube di Maps possono contenere tipi diversi di dati, ad esempio colori o normali, ma sono organizzate come sei trame sulle facce di un cubo. Per questo motivo, le mappe di cubo non vengono campionate fornendo coordinate di trama, ma un vettore la cui origine è il centro del cubo. Il campione viene acquisito in corrispondenza del punto in cui il vettore interseca il cubo. Le mappe cubo permettono di fornire un'approssimazione dell'ambiente che può essere usata per calcolare i riflessi, operazione chiamata *mapping dell'ambiente*, o per fornire a oggetti sferici una trama con una distorsione minore rispetto alle trame bidimensionali di base.

 Qualsiasi trama può essere codificata e compressa in diversi modi ortogonali al tipo di dati contenuti da una trama oppure alla dimensionalità o "forma" della trama. Tuttavia, metodi di codifica e compressione diversi producono risultati migliori a seconda del tipo di dati.

 È possibile usare l'editor di immagini per creare e modificare trame e immagini analogamente ad altri editor di immagini. L'editor di immagini offre anche mapping MIP e altre funzionalità da usare con la grafica 3D e supporta molti dei formati di trama con accelerazione hardware e compressione elevata supportati da DirectX.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Image Editor](../designers/image-editor.md)|Descrive come usare l'editor di immagini con trame e immagini.|
|[Esempi dell'editor immagini](../designers/image-editor-examples.md)|Contiene i collegamenti ad alcuni argomenti che descrivono come usare l'editor di immagini per eseguire attività comuni di elaborazione delle immagini.|

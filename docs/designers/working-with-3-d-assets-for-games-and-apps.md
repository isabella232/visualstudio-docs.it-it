---
title: Uso di risorse 3D per giochi e app
description: Informazioni sugli strumenti Visual Studio che è possibile usare per creare o modificare modelli, trame e shader 3D per giochi e app basati su DirectX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 1f4332e8eefb4c1d8c2ea5ce8d1b25eab840fcdd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073604"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Usare risorse 3D per giochi e app

Questo articolo descrive gli strumenti di Visual Studio che è possibile usare per creare o modificare modelli 3D, trame e shader per app e giochi DirectX.

## <a name="directx-app-development-in-visual-studio"></a>Sviluppo di app DirectX in Visual Studio

In genere un'app DirectX unisce logica di programmazione, API DirectX e i programmi HLSL (High Level Shading Language) ad audio e risorse visive 3D per offrire un'esperienza multimediale dettagliata e interattiva. Visual Studio include strumenti utili per lavorare con immagini, trame, modelli 3D e shader senza uscire dall'IDE per usare un altro strumento. Gli strumenti di Visual Studio sono particolarmente adatti per creare risorse *segnaposto* che è possibile usare per testare codice o creare prototipi prima di commissionare le risorse pronte per la produzione e per analizzare e modificare le risorse pronte per la produzione quando si esegue il debug dell'app.

Di seguito altre informazioni sui tipi di asset che è possibile usare in Visual Studio.

### <a name="images-and-textures"></a>Immagini e trame

Le immagini e le trame definiscono colore e dettagli visivi in giochi e app. Nella grafica 3D esistono trame di vari formati, tipi e geometrie per supportare diversi usi. Ad esempio, le mappe comuni offrono normali alla superficie per ogni pixel per un'illuminazione più dettagliata dei modelli 3D, mentre le mappe cubo offrono trama in tutte le direzioni per usi quali sky boxing, riflessi e mapping di trama sferica. Le trame offrono mappe MIP per supportare un rendering efficiente a livelli di dettaglio diversi e possono supportare canali e ordinamenti di colore diversi. Le trame possono essere archiviate in vari formati compressi che occupano meno memoria grafica dedicata e consentono alle GPU di accedere alle trame in modo più efficiente.

È possibile usare l'editor immagini di Visual Studio per lavorare con immagini e trame nei numerosi tipi e formati comuni.

### <a name="3d-models"></a>Modelli 3D

I modelli 3D creano spazio e forma in giochi e app. I modelli codificano la posizione dei punti nello spazio 3D, noti come *vertici*, insieme all'indicizzazione dati, per definire linee o triangoli che rappresentano la forma del modello. A questi vertici è possibile aggiungere dati aggiuntivi, ad esempio informazioni sul colore, vettori normali o attributi specifici dell'applicazione. Ogni modello può anche definire attributi a livello di oggetto, ad esempio quali shader usare per definire l'aspetto dell'area dell'oggetto o quale trama applicare.

È possibile usare l'Editor modello di Visual Studio per lavorare con modelli 3D in diversi formati comuni.

### <a name="shaders"></a>Shader

Gli shader sono piccoli programmi specifici di dominio che vengono eseguiti nell'unità di elaborazione grafica (GPU). Gli shader determinano quali modelli 3D vengono trasformati in forme su schermo e in che modo viene colorato ogni pixel contenuto in queste forme. Creando e applicando uno shader a un oggetto nel gioco o nell'app, è possibile assegnare all'oggetto un aspetto univoco.

È possibile usare la progettazione shader di Visual Studio, ovvero uno strumento di progettazione shader basato su grafico, per creare effetti visivi personalizzati senza conoscere la programmazione HLSL.

> [!NOTE]
> Per altre informazioni su come iniziare la programmazione DirectX, vedere [DirectX](/windows/win32/directx). Per altre informazioni su come eseguire il debug di un'app basata su DirectX, vedere Diagnostica della grafica [(debug della grafica DirectX).](../debugger/graphics/visual-studio-graphics-diagnostics.md)

## <a name="directx-version-compatibility"></a>Compatibilità tra versioni DirectX

Visual Studio usa DirectX per eseguire il rendering degli asset 2D e 3D. È possibile selezionare il renderer di DirectX 11 o il renderer software di WARP (Windows Advanced Rasterization Platform). Il renderer di DirectX 11 offre un rendering a prestazioni elevate e con accelerazione hardware in GPU DirectX 11 e DirectX 10. Il renderer WARP consente di verificare se le risorse usano un'ampia gamma di computer, tra cui computer senza hardware grafico moderno e computer con hardware grafico integrato. Per altre informazioni su WARP, vedere la [guida Windows Advanced Rasterization Platform (WARP)](/windows/win32/direct3darticles/directx-warp).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Uso di trame e immagini](../designers/working-with-textures-and-images.md)|Viene descritto come usare Visual Studio per lavorare con immagini e trame.|
|[Uso dei modelli 3D](../designers/working-with-3-d-models.md)|Viene descritto come usare Visual Studio per lavorare con i modelli 3D.|
|[Uso degli shader](../designers/working-with-shaders.md)|Viene descritto come usare la progettazione shader di Visual Studio per creare e modificare gli effetti di shader personalizzati.|
|[Uso di asset 3D nel gioco o nell'app](../designers/using-3-d-assets-in-your-game-or-app.md)|Viene descritto come usare le risorse, quali risorse sono state create con l'Editor immagini, l'Editor modello o la finestra di progettazione shader nel gioco o nell'app.|

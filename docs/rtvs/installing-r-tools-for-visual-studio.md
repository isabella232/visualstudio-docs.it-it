---
title: Installazione di R Tools
description: Come installare R Tools in Visual Studio 2017 e Visual Studio 2015, comprese le installazioni offline.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: 9abcdbe0c9e9f74b2e8d0424230100441804ed2a
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2021
ms.locfileid: "114679659"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Come installare R Tools per Visual Studio

Contenuto dell'articolo:

- [Versioni supportate di Visual Studio](#supported-versions-of-visual-studio)
- [Installare RTVS in Visual Studio 2017](#install-rtvs-in-visual-studio-2017)
- [Installare RTVS in Visual Studio 2015](#install-rtvs-in-visual-studio-2015)
- [Installazione offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Dopo aver installato R Tools, si potrebbe voler configurare Visual Studio per un layout Data Scientist ottimizzato, come descritto nell'articolo [Options](options-for-r-tools-in-visual-studio.md) (Opzioni).

## <a name="supported-versions-of-visual-studio"></a>Versioni supportate di Visual Studio

R Tools per Visual Studio (RTVS) è supportato in Windows con le edizioni Community (gratuita), Professional ed Enterprise di [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) e [Visual Studio 2015 Update 3 (o versioni successive)](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) (download diretto).

RTVS non è attualmente supportato in Visual Studio per Mac.

RTVS non viene installato se si ha solo Visual Studio Shell incluso in prodotti come Visual Studio Test Professional e SQL Server Management Studio. Visual Studio Shell non ha i componenti necessari per RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Installare RTVS in Visual Studio 2017

1. Eseguire il programma di installazione di Visual Studio e selezionare l'opzione **Modifica**. Per informazioni dettagliate, vedere [Modificare Visual Studio](../install/modify-visual-studio.md). Se Visual Studio non è ancora installato, vedere [Installare Visual Studio](../install/install-visual-studio.md). In Windows 7 verificare che il programma di installazione sia aggiornato in modo da visualizzare Visual Studio 2017 versione *15.2 build 26430.12* o versione successiva.

1. Selezionare il carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati**:

    ![Carico di lavoro delle applicazioni analitiche e di analisi scientifica dei dati in VS2017](media/installation-data-science-workload.png)

1. Impostare tutte le opzioni aggiuntive sul lato destro con lo stesso nome del carico di lavoro. Per impostazione predefinita, questo carico di lavoro include il supporto per F# e Python. Per R, i requisiti minimi sono il **supporto del linguaggio R**, il **supporto del runtime per lo sviluppo R** e **Microsoft R Client**.

RTVS è installato in: *%ProgramFiles(x86)%\Microsoft Visual Studio \<version> \<edition> Common7\IDE\Extensions\Microsoft\R Tools per Visual Studio dove è* in genere e è , o *\<version>* `2017` *\<edition>* `Community` `Professional` `Enterprise` .

## <a name="install-rtvs-in-visual-studio-2015"></a>Installare RTVS in Visual Studio 2015

Con Visual Studio 2015, è necessario installare separatamente un interprete di R e R Tools.

### <a name="install-an-r-interpreter"></a>Installare un interprete di R

RTVS richiede un'installazione a 64 bit di R versione 3.2.1 o successiva da una o da più origini seguenti:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open e CRAN R consentono l'uso di più versioni affiancate. Microsoft R Client supporta solo una versione e usa sempre la versione installata più recentemente.

### <a name="install-the-r-tools"></a>Installare R Tools

Scaricare la versione corrente di RTVS per Visual Studio 2015 da [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe) . RTVS verifica la disponibilità di una versione appropriata di Visual Studio e consente anche di installare un interprete di R, se non è già installato.

> [!Note]
> Il programma di installazione autonomo RTVS funziona solo con Visual Studio 2015. Per Visual Studio 2017, installare il supporto R tramite il [carico di lavoro delle applicazioni analitiche e di analisi scientifica dei dati](#install-rtvs-in-visual-studio-2017) come descritto in precedenza.

RTVS per Visual Studio 2015 è installato:`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Installazione offline di Visual Studio e RTVS

L'installazione offline è utile per i computer che non sono connessi a Internet:

1. Passare a [Creare un'installazione offline di Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Se si usa Visual Studio 2015, selezionare **2015** nel selettore sopra il sommario.

1. Seguire le istruzioni per la creazione di un'installazione offline nella pagina Web.

1. Per Visual Studio 2015, scaricare i programmi di installazione RTVS offline da [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) e [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip) .

1. Installare Visual Studio e RTVS da un programma di installazione offline.

## <a name="see-also"></a>Vedi anche

- [Introduzione a R](getting-started-with-r.md)
- [R Tools sample projects](getting-started-samples.md) (Progetti di esempio di R Tools)
- [Guida di R Tools](getting-started-help.md)
- [Opzioni di R Tools](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (in precedenza, R Server)](/machine-learning-server/)

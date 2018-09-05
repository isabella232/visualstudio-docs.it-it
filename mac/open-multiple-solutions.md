---
title: 'Procedura: Aprire più soluzioni'
description: Informazioni su come aprire più soluzioni in Visual Studio per Mac e su come aprire più istanze dell'applicazione.
author: conceptdev
ms.author: crdun
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.openlocfilehash: a8001e9511f0c8864792dba783368d03ee6eef81
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2018
ms.locfileid: "43223939"
---
# <a name="opening-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Apertura di più soluzioni o istanze di Visual Studio per Mac

Per impostazione predefinita, tutte le applicazioni in un Mac, incluso Visual Studio per Mac, sono app _a istanza singola_. Ciò significa che se l'applicazione che si vuole usare è già aperta (come indicato da un "punto" sotto l'icona nel Dock) e si fa di nuovo clic sull'icona, si apre l'istanza in esecuzione, anziché una nuova.  Se sono necessarie altre istanze dell'applicazione, è possibile richiedere al sistema di aprirle, come descritto nella [sezione successiva](#open-a-second-instance-of-visual-studio-for-mac).

Quando si apre una soluzione, poi, il comportamento predefinito corrisponde all'apertura della soluzione in una nuova area di lavoro e alla chiusura dell'area di lavoro corrente (se necessario). È possibile sostituire questo comportamento predefinito, mantenendo aperta l'area di lavoro corrente, come descritto nella sezione [Aprire una seconda soluzione](#open-a-second-solution-inside-a-single-instance).

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Aprire una seconda istanza di Visual Studio per Mac

Per aprire una seconda istanza dell'IDE, aprire l'applicazione **Terminale** e immettere la riga seguente:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Aprire una seconda soluzione all'interno di un'istanza singola

Per aprire una seconda soluzione insieme alla prima, procedere come segue:

1. Con la prima soluzione già aperta, selezionare **File > Apri**.
2. Sfogliare il file system per individuare la soluzione esistente.
3. Selezionare il file con estensione **sln** e premere il pulsante **Opzioni**:
    
    ![posizione del pulsante Opzioni](media/open-multiple-solutions-image3.png)
4. Deselezionare la casella **Chiudi l'area di lavoro corrente**:

    ![screenshot dell'area di lavoro corrente](media/open-multiple-solutions-image1.png)

1. Premere il pulsante Apri per aprire la seconda soluzione nel riquadro della soluzione.

**In alternativa**, se la soluzione è stata aperta di recente, è possibile usare la procedura seguente:

1. Passare alla voce di menu File > Soluzioni recenti:

    ![screenshot del menu Soluzioni recenti](media/open-multiple-solutions-image2.png)

1. Tenere premuto **Ctrl** e selezionare la soluzione. Questa combinazione consente di aprire la seconda soluzione nel riquadro della soluzione.

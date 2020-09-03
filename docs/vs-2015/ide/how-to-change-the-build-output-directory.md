---
title: 'Procedura: Modificare la directory di output della compilazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b665f5788d12c294e8ab7f55ecc63d183030a0ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645436"
---
# <a name="how-to-change-the-build-output-directory"></a>Procedura: modificare la directory dell'output compilato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il percorso dell'output generato dal progetto può essere specificato a livello di singole configurazioni (per debug e/o rilascio).

> [!NOTE]
> Se si dispone di un progetto di **installazione** , vedere la nota alla fine di questo articolo.

## <a name="changing-the-build-output-directory"></a>Modifica della directory dell'output di compilazione

#### <a name="to-change-the-build-output-directory"></a>Per modificare la directory dell'output di compilazione

1. Nella barra dei menu scegliere **Progetto**, *NomeApp* **Proprietà**. In alternativa, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**.

2. Se si dispone di un progetto di Visual Basic, selezionare la scheda **Compila** . Se si dispone di un progetto Visual C#, selezionare la scheda **Compila** . Se si dispone di un progetto C++ o di un progetto JavaScript, selezionare la scheda **generale** .

3. Nell'elenco a discesa della configurazione nella parte superiore, scegliere la configurazione per cui si vuole modificare il percorso di output (debug, rilascio o tutte).

     Trovare la voce del percorso di output (**percorso dell'output di compilazione** in Visual Basic, directory di **output** in Visual C++, **percorso di output** in JavaScript e C#). Specificare una nuova directory dell'output di compilazione relativa alla directory del progetto.

> [!NOTE]
> In un progetto di installazione, la casella **Nome file di output** modifica solo il percorso del file Setup.exe file, non il percorso dei file di progetto. Per ulteriori informazioni, vedere **compilazione, proprietà di configurazione, finestra di dialogo Proprietà progetto di distribuzione**.

## <a name="see-also"></a>Vedere anche
 [Pagina compilazione, Progettazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md) [pagina delle proprietà generale (progetto)](https://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45) [compilazione e compilazione](../ide/compiling-and-building-in-visual-studio.md)

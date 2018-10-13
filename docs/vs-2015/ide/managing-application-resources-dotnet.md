---
title: Gestione delle risorse delle applicazioni (.NET) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b29f32fa59f719af3efab6901596b682c95a5d57
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287222"
---
# <a name="managing-application-resources-net"></a>Gestione delle risorse delle applicazioni (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I file di risorse sono file che fanno parte di un'applicazione ma non vengono compilati, ad esempio file di icone o file audio. Poiché questi file non fanno parte del processo di compilazione, è possibile modificarli senza dover ricompilare i file binari. Se si prevede di localizzare l'applicazione, è consigliabile usare file di risorse per tutte le stringhe e le altre risorse che devono essere modificate quando si localizza l'applicazione.  
  
 Per altre informazioni sulle risorse nelle app desktop .NET, vedere [Risorse nelle applicazioni desktop](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890). Per altre informazioni sulle risorse nelle app desktop C++, vedere [Working with Resource Files](http://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780).  
  
 Le app di Windows Store usano un modello di risorse diverso rispetto alle app desktop. Per informazioni sulle risorse nelle app di Windows Store, vedere [Definizione delle risorse delle applicazioni](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) sul sito Web Windows Dev Center.  
  
## <a name="working-with-resources"></a>Uso delle risorse  
 Aprire la finestra delle proprietà del progetto in un progetto di codice gestito. A questo scopo, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**oppure digitare **proprietà del progetto** nella finestra **Avvio veloce** o premere ALT+INVIO nella finestra **Esplora soluzioni** . Selezionare la scheda **Risorse** . È possibile aggiungere un file RESX, se non è ancora presente nel progetto, aggiungere ed eliminare diversi tipi di risorse e modificare le risorse esistenti.  
  
 Per informazioni su come usare le risorse nei progetti C++, vedere [How to: Create a Resource](http://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716) (Procedura: Creare una risorsa).


---
title: Gestione delle risorse delle applicazioni (.NET) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b599a919911fcc5d2833cfe69b75f7b32cced858
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="managing-application-resources-net"></a>Gestione delle risorse delle applicazioni (.NET)
I file di risorse sono file che fanno parte di un'applicazione ma non vengono compilati, ad esempio file di icone o file audio. Poiché questi file non fanno parte del processo di compilazione, è possibile modificarli senza dover ricompilare i file binari. Se si prevede di localizzare l'applicazione, è consigliabile usare file di risorse per tutte le stringhe e le altre risorse che devono essere modificate quando si localizza l'applicazione.  
  
Per altre informazioni sulle risorse nelle app desktop .NET, vedere [Resources in Desktop Apps](/dotnet/framework/resources/index). Per altre informazioni sulle risorse nelle app desktop C++, vedere [Working with Resource Files](/cpp/windows/working-with-resource-files).  
  
Le app UWP usano un modello di risorse diverso rispetto alle applicazioni desktop. Per informazioni sulle risorse nelle app di Windows 8.x, vedere [Definizione delle risorse delle app (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx).  
  
## <a name="working-with-resources"></a>Uso delle risorse  
In un progetto di codice gestito aprire la finestra delle proprietà del progetto. È possibile aprire la finestra delle proprietà in uno dei modi seguenti:

- fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e selezionare **Proprietà**
- digitare **proprietà progetto** nella finestra **Avvio veloce**
- scegliere **ALT+INVIO** nella finestra **Esplora soluzioni**

Selezionare la scheda **Risorse** . È possibile aggiungere un file RESX, se non è ancora presente nel progetto, aggiungere ed eliminare diversi tipi di risorse e modificare le risorse esistenti.  
  
Per informazioni su come usare le risorse nei progetti C++, vedere [How to: Create a Resource](/cpp/windows/how-to-create-a-resource).
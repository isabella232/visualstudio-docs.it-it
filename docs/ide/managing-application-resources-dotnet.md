---
title: Gestire le risorse dell'applicazione (.NET)
description: Informazioni su come gestire i file di risorse dell'applicazione che non fanno parte del processo di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 16d60ac11edc8b75779c0d3bd57d1e9d0dfa369bbb59a8dd769b73da2648e845
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357817"
---
# <a name="manage-application-resources-net"></a>Gestire le risorse dell'applicazione (.NET)

I file di risorse sono file che fanno parte di un'applicazione ma non vengono compilati, ad esempio file di icone o file audio. Poiché questi file non fanno parte del processo di compilazione, è possibile modificarli senza dover ricompilare i file binari. Se si prevede di localizzare l'applicazione, è consigliabile usare file di risorse per tutte le stringhe e le altre risorse che devono essere modificate quando si localizza l'applicazione.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Gestione delle risorse delle app (Visual Studio per Mac)](/visualstudio/mac/managing-app-resources).

Per altre informazioni sulle risorse nelle app .NET, vedere [Risorse nelle app .NET.](/dotnet/framework/resources/index)

## <a name="work-with-resources"></a>Uso delle risorse

In un progetto di codice gestito aprire la finestra delle proprietà del progetto. È possibile aprire la finestra delle proprietà in uno dei modi seguenti:

- Fare clic con il pulsante destro del mouse sul **nodo Esplora soluzioni** progetto e scegliere **Proprietà**
- Digitazione di **proprietà progetto** nella casella di ricerca **CTRL**+**Q**
- Scelta **di ALT** + **INVIO** in **Esplora soluzioni**

Selezionare la **scheda** Risorse. È possibile aggiungere un file con estensione *resx* se il progetto non ne contiene già uno, aggiungere ed eliminare diversi tipi di risorse e modificare le risorse esistenti.

## <a name="resources-in-other-project-types"></a>Risorse in altri tipi di progetto

Le risorse vengono gestite in modo diverso nei progetti .NET rispetto ad altri tipi di progetto. Per altre informazioni sulle risorse in:

- app della piattaforma UWP (Universal Windows Platform), vedere [Risorse dell'app e sistema di gestione delle risorse](/windows/uwp/app-resources/)
- Progetti C++, vedere [Utilizzare file di risorse](/cpp/windows/working-with-resource-files) e [Procedura: creare una risorsa](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Vedi anche

- [Risorse nelle app .NET (.NET Framework)](/dotnet/framework/resources/index)
- [Gestione delle risorse delle app (Visual Studio per Mac)](/visualstudio/mac/managing-app-resources)

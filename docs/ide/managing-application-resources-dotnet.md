---
title: Gestire le risorse dell'applicazione (.NET)
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29e4fbbd8d50001807f3d90a82d18e40a3674d01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654254"
---
# <a name="manage-application-resources-net"></a>Gestire le risorse dell'applicazione (.NET)

I file di risorse sono file che fanno parte di un'applicazione ma non vengono compilati, ad esempio file di icone o file audio. Poiché questi file non fanno parte del processo di compilazione, è possibile modificarli senza dover ricompilare i file binari. Se si prevede di localizzare l'applicazione, è consigliabile usare file di risorse per tutte le stringhe e le altre risorse che devono essere modificate quando si localizza l'applicazione.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Gestione delle risorse delle app (Visual Studio per Mac)](/visualstudio/mac/managing-app-resources).

Per altre informazioni sulle risorse nelle app desktop .NET, vedere [Risorse nelle applicazioni desktop](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Uso delle risorse

In un progetto di codice gestito aprire la finestra delle proprietà del progetto. È possibile aprire la finestra delle proprietà in uno dei modi seguenti:

- Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e selezionare **Proprietà**
- Digitazione di **proprietà progetto** nella casella di ricerca **CTRL**+**Q**
- Scegliere **ALT**+**INVIO** in **Esplora soluzioni**

Selezionare la scheda **risorse** . È possibile aggiungere un file con *estensione resx* se il progetto non ne contiene già uno, aggiungere ed eliminare diversi tipi di risorse e modificare le risorse esistenti.

## <a name="resources-in-other-project-types"></a>Risorse in altri tipi di progetto

Le risorse vengono gestite in modo diverso nei progetti .NET rispetto ad altri tipi di progetto. Per altre informazioni sulle risorse in:

- app della piattaforma UWP (Universal Windows Platform), vedere [Risorse dell'app e sistema di gestione delle risorse](/windows/uwp/app-resources/)
- Progetti C++, vedere [Utilizzare file di risorse](/cpp/windows/working-with-resource-files) e [Procedura: creare una risorsa](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Vedere anche

- [Risorse nelle applicazioni desktop (.NET Framework)](/dotnet/framework/resources/index)
- [Gestione delle risorse delle app (Visual Studio per Mac)](/visualstudio/mac/managing-app-resources)

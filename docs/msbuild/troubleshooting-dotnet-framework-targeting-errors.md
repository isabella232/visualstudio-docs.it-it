---
title: Risoluzione dei problemi relativi agli errori di impostazione di .NET Framework come destinazione | Microsoft Docs
description: Informazioni su MSBuild che potrebbero verificarsi a causa di problemi di riferimento e su come risolverli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- dotnet
ms.openlocfilehash: a4f5af72bbc0a377b7876b858b58cffdaedff3391fda17f8df92a33cb94f7042
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369722"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Risolvere i problemi relativi agli errori di impostazione di .NET Framework come destinazione

Questo argomento illustra gli errori di MSBuild che possono verificarsi a causa di problemi di riferimento e indica in che modo è possibile risolvere tali errori.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>È stato fatto riferimento a un progetto o a un assembly destinato a una versione diversa di .NET Framework

 È possibile creare applicazioni che fanno riferimento a progetti o assembly destinati a versioni diverse di .NET Framework. È ad esempio possibile creare un'applicazione destinata al profilo client per .NET Framework 4 ma che fa riferimento a un assembly destinato a .NET Framework 2.0. Se tuttavia si crea un progetto destinato a una versione precedente di .NET Framework, non è possibile impostare in tale progetto un riferimento a un progetto o a un assembly destinato al profilo client per .NET Framework 4 o per .NET Framework 4 stesso. Per correggere l'errore, assicurarsi che l'applicazione abbia come destinazione profili compatibili con il profilo di destinazione dei progetti o degli assembly a cui fa riferimento.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Come nuova destinazione di un progetto è stata definita una versione diversa di .NET Framework

 Se si modifica la versione di destinazione di .NET Framework per l'applicazione, Visual Studio modifica alcuni dei riferimenti. Può tuttavia essere necessario aggiornarne altri in modo manuale. Ad esempio, uno degli errori indicati in precedenza potrebbe verificarsi se si modifica un'applicazione in modo che abbia come destinazione il Service Pack 1 di .NET Framework 3.5 e tale applicazione abbia risorse o impostazioni che si basano sul profilo client per .NET Framework 4.

 Per ovviare alle impostazioni, aprire **Esplora soluzioni**, scegliere **Mostra tutti i file** e quindi modificare il file *app.config* nell'editor XML di Visual Studio. Nelle impostazioni modificare la versione in modo che corrisponda alle versione corretta di .NET Framework. È ad esempio possibile modificare l'impostazione della versione da 4.0.0.0 a 2.0.0.0. Analogamente, per un'applicazione che ha aggiunto risorse, aprire **Esplora soluzioni**, scegliere il pulsante **Mostra tutti i file**, espandere **Progetti** (Visual Basic) o **Proprietà** (C#) e quindi modificare il file *Resources.resx* nell'editor XML di Visual Studio. Modificare l'impostazione della versione da 4.0.0.0 a 2.0.0.0.

 Se l'applicazione dispone di risorse, come icone o bitmap, o di impostazioni, come stringhe di connessione dati, per correggere l'errore è anche possibile rimuovere tutti gli elementi nella pagina **Impostazioni** di **Creazione progetti** e quindi aggiungere di nuovo le impostazioni necessarie.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Come nuova destinazione di un progetto è stata definita una versione diversa di .NET Framework e non è possibile risolvere i riferimenti

 Se come nuova destinazione di un progetto è stata definita una versione diversa di .NET Framework, in alcuni casi è possibile che i riferimenti non vengano risolti correttamente. I riferimenti espliciti completi agli assembly generano spesso questo problema. È tuttavia possibile correggere l'errore rimuovendo i riferimenti non risolti e quindi aggiungendoli di nuovo al progetto. In alternativa, è possibile modificare il file di progetto per sostituire i riferimenti. Rimuovere innanzitutto i riferimenti nel formato seguente:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Sostituirli quindi con il formato semplice seguente:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Dopo aver chiuso e riaperto il progetto, è necessario ricompilarlo per verificare che tutti i riferimenti vengano risolti correttamente.

## <a name="see-also"></a>Vedi anche

- [Procedura: Scegliere una versione di .NET Framework di destinazione](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework profilo client](/dotnet/framework/deployment/client-profile)
- [Panoramica sull'impostazione dei framework di destinazione](../ide/visual-studio-multi-targeting-overview.md)
- [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)

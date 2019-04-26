---
title: 'Procedura: Specificare quale destinazione compilare per prima | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28a533fff657e9e6cf426124bf65068f15190e7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997369"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Procedura: Specificare quale destinazione compilare per prima
Un file di progetto può contenere uno o più elementi `Target` che definiscono come viene compilato il progetto. Il motore [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) compila il primo progetto che trova e le eventuali dipendenze, a meno che il file di progetto non contenga un attributo `DefaultTargets` o `InitialTargets` o non venga specificata una destinazione nella riga di comando usando l'opzione **-target**.

## <a name="use-the-initialtargets-attribute"></a>Usare l'attributo InitialTargets
 L'attributo `InitialTargets` dell'elemento `Project` specifica una destinazione che verrà eseguita per prima, anche se vengono specificate destinazioni nella riga di comando o nell'attributo `DefaultTargets`.

#### <a name="to-specify-one-initial-target"></a>Per specificare una destinazione iniziale

- Specificare la destinazione predefinita nell'attributo `InitialTargets` dell'elemento `Project`. Ad esempio:

   `<Project InitialTargets="Clean">`

  È possibile specificare più di una destinazione iniziale nell'attributo `InitialTargets` elencando le destinazioni in ordine e usando il punto e virgola per separare ogni destinazione. Le destinazioni nell'elenco verranno eseguite in sequenza.

#### <a name="to-specify-more-than-one-initial-target"></a>Per specificare più di una destinazione iniziale

- Elencare le destinazioni iniziali, separate da punto e virgola, nell'attributo `InitialTargets` dell'elemento `Project`. Ad esempio, per eseguire la destinazione `Clean` e poi la destinazione `Compile`, digitare:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Usare l'attributo DefaultTargets
 L'attributo `DefaultTargets` dell'elemento `Project` specifica la destinazione o le destinazioni che vengono compilate se non viene specificata una destinazione in modo esplicito nella riga di comando. Se vengono specificate destinazioni sia nell'attributo `InitialTargets` che nell'attributo `DefaultTargets` e nessuna destinazione viene specificata nella riga di comando, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] esegue le destinazioni specificate nell'attributo `InitialTargets` seguito dalle destinazioni specificate nell'attributo `DefaultTargets`.

#### <a name="to-specify-one-default-target"></a>Per specificare una destinazione predefinita

- Specificare la destinazione predefinita nell'attributo `DefaultTargets` dell'elemento `Project`. Ad esempio:

   `<Project DefaultTargets="Compile">`

  È possibile specificare più di una destinazione predefinita nell'attributo `DefaultTargets` elencando le destinazioni in ordine e usando il punto e virgola per separare ogni destinazione. Le destinazioni nell'elenco verranno eseguite in sequenza.

#### <a name="to-specify-more-than-one-default-target"></a>Per specificare più di una destinazione predefinita

- Elencare le destinazioni predefinite, separate da punto e virgola, nell'attributo `DefaultTargets` dell'elemento `Project`. Ad esempio, per eseguire la destinazione `Clean` e poi la destinazione `Compile`, digitare:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Usare l'opzione -target
 Se nel file di progetto non è definita una destinazione predefinita o se non si vuole usare la destinazione predefinita, è possibile usare l'opzione della riga di comando **-target** per specificare un'altra destinazione. Vengono eseguite le destinazioni specificate con l'opzione **-target** invece delle destinazioni specificate dall'attributo `DefaultTargets`. Le destinazioni specificate nell'attributo `InitialTargets` vengono eseguite sempre per prime.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Per usare per prima una destinazione diversa da quella predefinita

- Specificare la destinazione da usare per prima tramite l'opzione della riga di comando **-target**. Ad esempio:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Per usare per prime più destinazioni diverse da quelle predefinite

- Elencare le destinazioni, separate da punto e virgola o virgola, usando l'opzione della riga di comando **-target**. Ad esempio:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Vedere anche
  [MSBuild](../msbuild/msbuild.md)
- [Destinazioni](../msbuild/msbuild-targets.md)
- [Procedura: Pulire una compilazione](../msbuild/how-to-clean-a-build.md)

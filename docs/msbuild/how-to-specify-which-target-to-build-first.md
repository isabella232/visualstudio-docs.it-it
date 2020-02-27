---
title: 'Procedura: Specificare quale destinazione compilare per prima'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e008e3181cd7c633179f35e7639265a2495fafe2
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633798"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Procedura: Specificare quale destinazione compilare per prima

Un file di progetto può contenere uno o più elementi `Target` che definiscono come viene compilato il progetto. Il motore di Microsoft Build Engine (MSBuild) compila il primo progetto trovato e tutte le dipendenze, a meno che il file di progetto non contenga un attributo `DefaultTargets`, un attributo `InitialTargets` o una destinazione sia specificato dalla riga di comando usando l'opzione **-target** .
## <a name="use-the-initialtargets-attribute"></a>Usare l'attributo InitialTargets

 L'attributo `InitialTargets` dell'elemento `Project` specifica una destinazione che verrà eseguita per prima, anche se vengono specificate destinazioni nella riga di comando o nell'attributo `DefaultTargets`.
L'attributo `InitialTargets` dell'elemento `Project` specifica una destinazione che verrà eseguita per prima, anche se vengono specificate destinazioni nella riga di comando o nell'attributo `DefaultTargets`.

#### <a name="to-specify-one-initial-target"></a>Per specificare una destinazione iniziale

- Specificare la destinazione predefinita nell'attributo `InitialTargets` dell'elemento `Project`. Ad esempio,

   `<Project InitialTargets="Clean">`

  È possibile specificare più di una destinazione iniziale nell'attributo `InitialTargets` elencando le destinazioni in ordine e usando il punto e virgola per separare ogni destinazione. Le destinazioni nell'elenco verranno eseguite in sequenza.

#### <a name="to-specify-more-than-one-initial-target"></a>Per specificare più di una destinazione iniziale

- Elencare le destinazioni iniziali, separate da punto e virgola, nell'attributo `InitialTargets` dell'elemento `Project`. Ad esempio, per eseguire la destinazione `Clean` e poi la destinazione `Compile`, digitare:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Usare l'attributo DefaultTargets

 L'attributo `DefaultTargets` dell'elemento `Project` specifica la destinazione o le destinazioni che vengono compilate se non viene specificata una destinazione in modo esplicito nella riga di comando. Se vengono specificate destinazioni negli attributi `InitialTargets` e `DefaultTargets` e nella riga di comando non è specificata alcuna destinazione, MSBuild esegue le destinazioni specificate nell'attributo `InitialTargets` seguito dalle destinazioni specificate nell'attributo `DefaultTargets`.

#### <a name="to-specify-one-default-target"></a>Per specificare una destinazione predefinita

- Specificare la destinazione predefinita nell'attributo `DefaultTargets` dell'elemento `Project`. Ad esempio,

   `<Project DefaultTargets="Compile">`

  È possibile specificare più di una destinazione predefinita nell'attributo `DefaultTargets` elencando le destinazioni in ordine e usando il punto e virgola per separare ogni destinazione. Le destinazioni nell'elenco verranno eseguite in sequenza.

#### <a name="to-specify-more-than-one-default-target"></a>Per specificare più di una destinazione predefinita

- Elencare le destinazioni predefinite, separate da punto e virgola, nell'attributo `DefaultTargets` dell'elemento `Project`. Ad esempio, per eseguire la destinazione `Clean` e poi la destinazione `Compile`, digitare:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Usare l'opzione -target

 Se nel file di progetto non è definita una destinazione predefinita o se non si vuole usare la destinazione predefinita, è possibile usare l'opzione della riga di comando **-target** per specificare un'altra destinazione. Vengono eseguite le destinazioni specificate con l'opzione **-target** invece delle destinazioni specificate dall'attributo `DefaultTargets`. Le destinazioni specificate nell'attributo `InitialTargets` vengono eseguite sempre per prime.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Per usare per prima una destinazione diversa da quella predefinita

- Specificare la destinazione da usare per prima tramite l'opzione della riga di comando **-target**. Ad esempio,

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Per usare per prime più destinazioni diverse da quelle predefinite

- Elencare le destinazioni, separate da punto e virgola o virgola, usando l'opzione della riga di comando **-target**. Ad esempio,

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Vedere anche

- [MSBuild](../msbuild/msbuild.md)
- [Server di destinazione](../msbuild/msbuild-targets.md)
- [Procedura: Pulire una compilazione](../msbuild/how-to-clean-a-build.md)

---
title: '&lt;Elemento RelatedProducts &gt; (programma di avvio automatico) | Microsoft Docs'
description: L'elemento RelatedProducts definisce altri prodotti che dipendono o sono inclusi nel prodotto corrente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: cb217da984fd23acdedc446724984d667e0006bf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120751"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;Elemento RelatedProducts &gt; (programma di avvio automatico)
`RelatedProducts`L'elemento definisce altri prodotti che dipendono da o sono inclusi nel prodotto corrente.

## <a name="syntax"></a>Sintassi

```xml
<RelatedProducts>
    <DependsOnProduct
        Code
    />
    <EitherProducts>
        <DependsOnProduct
            Code
        />
    </EitherProducts>
    <IncludesProduct
        Code
    />
</RelatedProducts>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `RelatedProducts`L'elemento è figlio `Product` dell'elemento . Non dispone di attributi.

## <a name="dependsonproduct"></a>DependsOnProduct
 L'elemento indica che il prodotto corrente dipende dal prodotto denominato e che il prodotto denominato deve `DependsOnProduct` essere installato prima di quello corrente. È un elemento figlio `RelatedProducts` dell'elemento . Un `RelatedProducts` elemento può avere uno o più elementi `DependsOnProduct` .

 `DependsOnProduct` ha l'attributo seguente.

|Attributo|Descrizione|
|---------------|-----------------|
|`Code`|Nome in codice del prodotto incluso, come specificato `ProductCode` dall'attributo `Product` dell'elemento . Per altre informazioni, vedere [ \<Product> Elemento](../deployment/product-element-bootstrapper.md).|

## <a name="eitherproducts"></a>EitherProducts
 `EitherProducts`L'elemento definisce zero o più elementi e non ha `DependsOnProduct` attributi. Almeno uno `DependsOnProduct` di questi set deve essere installato prima del prodotto corrente. Un `RelatedProducts` elemento può avere zero o più `EitherProducts` elementi.

## <a name="includesproduct"></a>IncludesProduct
 `IncludesProduct`L'elemento indica che un prodotto è incluso nell'installazione corrente e non richiede un'installazione separata. È un elemento figlio `RelatedProducts` dell'elemento . Un `RelatedProducts` elemento può avere uno o più elementi `IncludesProduct` .

 `IncludesProduct` ha l'attributo seguente.

|Attributo|Descrizione|
|---------------|-----------------|
|`Code`|Nome in codice del prodotto incluso, come specificato `ProductCode` dall'attributo `Product` dell'elemento . Per altre informazioni, vedere [ \<Product> Elemento](../deployment/product-element-bootstrapper.md).|

## <a name="example"></a>Esempio
 L'esempio di codice seguente specifica che Microsoft Installer è installato con il .NET Framework e pertanto non sarà necessaria un'installazione separata.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>Vedi anche
- [\<Product> Elemento](../deployment/product-element-bootstrapper.md)
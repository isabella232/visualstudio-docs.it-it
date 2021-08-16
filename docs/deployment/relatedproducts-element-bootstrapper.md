---
title: '&lt;Elemento RelatedProducts &gt; (bootstrapper) | Microsoft Docs'
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
ms.openlocfilehash: 0cceb38026a3c5c7241477f167cec1bb5a08f8f3524ac7157c79ec72d9de3d81
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121263283"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;Elemento RelatedProducts &gt; (programma di avvio automatico)
`RelatedProducts`L'elemento definisce altri prodotti che dipendono o sono inclusi nel prodotto corrente.

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
 `RelatedProducts`L'elemento è un elemento figlio dell'elemento `Product` . Non ha attributi.

## <a name="dependsonproduct"></a>DependsOnProduct
 L'elemento indica che il prodotto corrente dipende dal prodotto denominato e che il prodotto denominato deve essere `DependsOnProduct` installato prima di quello corrente. È un elemento figlio `RelatedProducts` dell'elemento . Un `RelatedProducts` elemento può avere uno o più `DependsOnProduct` elementi.

 `DependsOnProduct` ha l'attributo seguente.

|Attributo|Descrizione|
|---------------|-----------------|
|`Code`|Nome in codice del prodotto incluso, come specificato `ProductCode` dall'attributo `Product` dell'elemento . Per altre informazioni, vedere [ \<Product> Elemento](../deployment/product-element-bootstrapper.md).|

## <a name="eitherproducts"></a>EitherProducts
 `EitherProducts`L'elemento definisce zero o più elementi e non dispone di `DependsOnProduct` attributi. Almeno uno `DependsOnProduct` in questo set deve essere installato prima del prodotto corrente. Un `RelatedProducts` elemento può avere zero o più `EitherProducts` elementi.

## <a name="includesproduct"></a>IncludesProduct
 `IncludesProduct`L'elemento indica che un prodotto è incluso nell'installazione corrente e non richiede un'installazione separata. È un elemento figlio `RelatedProducts` dell'elemento . Un `RelatedProducts` elemento può avere uno o più `IncludesProduct` elementi.

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
---
title: '&lt;RelatedProducts&gt; elemento (programma di avvio automatico) | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e04cc8a351ed99ec0b477b2db5052ac94b56054
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036134"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; elemento (programma di avvio automatico)
Il `RelatedProducts` elemento definisce gli altri prodotti dipendono o sono inclusi nel prodotto corrente.  
  
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
 Il `RelatedProducts` elemento è figlio di `Product` elemento. Non dispone di attributi.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 Il `DependsOnProduct` elemento indica che il prodotto corrente dipende dal prodotto specificato e che il prodotto deve essere installato prima di quello corrente. È un figlio di `RelatedProducts` elemento. Oggetto `RelatedProducts` elemento può contenere uno o più `DependsOnProduct` elementi.  
  
 `DependsOnProduct` ha l'attributo seguente.  
  
|Attributo|Description|  
|---------------|-----------------|  
|`Code`|Il nome del prodotto incluso, come specificato dal codice il `ProductCode` attributo del `Product` elemento. Per altre informazioni, vedere [ \<prodotto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 Il `EitherProducts` elemento definisce zero o più `DependsOnProduct` elementi, e non include attributi. Almeno un `DependsOnProduct` in questo set deve essere installato prima del prodotto corrente. Oggetto `RelatedProducts` può contenere zero o più `EitherProducts` elementi.  
  
## <a name="includesproduct"></a>IncludesProduct  
 Il `IncludesProduct` elemento indica che un prodotto sia incluso nell'installazione corrente e non richiede un'installazione separata. È un figlio di `RelatedProducts` elemento. Oggetto `RelatedProducts` elemento può contenere uno o più `IncludesProduct` elementi.  
  
 `IncludesProduct` ha l'attributo seguente.  
  
|Attributo|Description|  
|---------------|-----------------|  
|`Code`|Il nome del prodotto incluso, come specificato dal codice il `ProductCode` attributo del `Product` elemento. Per altre informazioni, vedere [ \<prodotto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente specifica che sia installato Microsoft Installer con la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]e pertanto non richiede un'installazione separata.  
  
```xml  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [\<Product > elemento](../deployment/product-element-bootstrapper.md)
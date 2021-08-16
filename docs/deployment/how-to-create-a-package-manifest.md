---
title: Creare un manifesto del pacchetto | Microsoft Docs
description: Informazioni sull'uso di un pacchetto del programma di avvio automatico per distribuire i prerequisiti per l ClickOnce appliazione, che contiene un manifesto del pacchetto per ogni impostazione locale.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 077926f3e2649a9e3fa49d39168e89e73c0af9fd313afe32bbfd8c20602d7609
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435491"
---
# <a name="how-to-create-a-package-manifest"></a>Procedura: Creare un manifesto del pacchetto
Per distribuire i prerequisiti per l'applicazione, è possibile usare un pacchetto del programma di avvio automatico. Un pacchetto del programma di avvio automatico contiene un singolo file manifesto del prodotto, ma un manifesto del pacchetto per ogni impostazione locale. La funzionalità condivisa tra versioni localizzate diverse deve essere insito nel manifesto del prodotto.

 Per altre informazioni sui manifesti del prodotto, vedere [Procedura: Creare un manifesto del prodotto.](../deployment/how-to-create-a-product-manifest.md)

## <a name="create-the-package-manifest"></a>Creare il manifesto del pacchetto

#### <a name="to-create-the-package-manifest"></a>Per creare il manifesto del pacchetto

1. Creare una directory per il pacchetto del programma di avvio automatico. Questo esempio viene usato *c:\package*.

2. Creare una sottodirectory con il nome delle impostazioni locali, ad esempio *en* per l'inglese.

3. In Visual Studio creare un file XML denominato *package.xml* e salvarlo nella cartella *C:\package\en.*

4. Aggiungere XML per elencare il nome del pacchetto del programma di avvio automatico, le impostazioni cultura per il manifesto del pacchetto localizzato e il contratto di licenza facoltativo. Nel codice XML seguente vengono utilizzate `DisplayName` le variabili e , definite in un elemento `Culture` successivo.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Aggiungere XML per elencare tutti i file presenti nella directory specifica delle impostazioni locali. Il codice XML seguente usa un file denominato *eula.txt* applicabile per le impostazioni **locali en.**

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Aggiungere codice XML per definire stringhe localizzabili per il pacchetto del programma di avvio automatico. Il codice XML seguente aggiunge stringhe di errore per le **impostazioni locali en.**

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. Copiare *la cartella C:\package* nella directory del Visual Studio bootstrapper. Ad Visual Studio 2010, si tratta della directory *\Programmi\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.*

## <a name="example"></a>Esempio
 Il manifesto del pacchetto contiene informazioni specifiche delle impostazioni locali, ad esempio messaggi di errore, condizioni di licenza software e Language Pack.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.txt">

  <PackageFiles>
    <PackageFile Name="eula.txt"/>
  </PackageFiles>

  <Strings>
    <String Name="DisplayName">Custom Bootstrapper Package</String>
    <String Name="Culture">en</String>
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>
    <String Name="GeneralFailure">A general error has occurred while
installing this package.</String>
  </Strings>
</Package>
```

## <a name="see-also"></a>Vedi anche
- [Informazioni di riferimento sullo schema di prodotti e pacchetti](../deployment/product-and-package-schema-reference.md)
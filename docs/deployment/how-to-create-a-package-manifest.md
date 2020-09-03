---
title: 'Procedura: creare un manifesto del pacchetto | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc3a1263136fe4c50b2c7020e1557a7a693691b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382523"
---
# <a name="how-to-create-a-package-manifest"></a>Procedura: Creare un manifesto del pacchetto
Per distribuire i prerequisiti per l'applicazione, è possibile usare un pacchetto del programma di avvio automatico. Un pacchetto del programma di avvio automatico contiene un singolo file manifesto del prodotto, ma un manifesto del pacchetto per ogni impostazione locale. Le funzionalità condivise tra diverse versioni localizzate dovrebbero essere inserite nel manifesto del prodotto.

 Per ulteriori informazioni sui manifesti del prodotto, vedere [procedura: creare un manifesto del prodotto](../deployment/how-to-create-a-product-manifest.md).

## <a name="create-the-package-manifest"></a>Creazione del manifesto del pacchetto

#### <a name="to-create-the-package-manifest"></a>Per creare il manifesto del pacchetto

1. Creare una directory per il pacchetto del programma di avvio automatico. Questo esempio viene usato *c:\package*.

2. Creare una sottodirectory con il nome delle impostazioni locali, ad esempio *en* per la lingua inglese.

3. In Visual Studio creare un file XML denominato *package.xml*e salvarlo nella cartella *C:\package\en* .

4. Aggiungere il codice XML per elencare il nome del pacchetto del programma di avvio automatico, le impostazioni cultura per questo manifesto del pacchetto localizzato e il contratto di licenza facoltativo. Nel codice XML seguente vengono utilizzate le variabili `DisplayName` e `Culture` , definite in un elemento successivo.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Aggiungere XML per elencare tutti i file presenti nella directory specifica delle impostazioni locali. Nel codice XML seguente viene utilizzato un file denominato *eula.txt* applicabile per le impostazioni locali **en** .

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Aggiungere il codice XML per definire le stringhe localizzabili per il pacchetto del programma di avvio automatico. Nel codice XML seguente vengono aggiunte stringhe di errore per le impostazioni locali **en** .

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

7. Copiare la cartella *C:\package* nella directory del programma di avvio automatico di Visual Studio. Per Visual Studio 2010, si tratta della directory *\Programmi\microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*

## <a name="example"></a>Esempio
 Il manifesto del pacchetto contiene informazioni specifiche delle impostazioni locali, ad esempio i messaggi di errore, le condizioni di licenza software e i Language Pack.

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

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema del prodotto e del pacchetto](../deployment/product-and-package-schema-reference.md)
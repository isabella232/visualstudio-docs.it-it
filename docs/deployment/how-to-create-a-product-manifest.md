---
title: Creare un manifesto del prodotto | Microsoft Docs
description: Informazioni su come distribuire i prerequisiti per l'applicazione ClickOnce con un pacchetto che contiene un singolo manifesto del prodotto e un manifesto del pacchetto per ogni impostazione locale.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: e58dbabb15b0d0a3643b38693d614aaf16a4a60c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160738"
---
# <a name="how-to-create-a-product-manifest"></a>Procedura: Creare il manifesto di un prodotto
Per distribuire i prerequisiti per l'applicazione, è possibile creare un pacchetto del programma di avvio automatico. Un pacchetto del programma di avvio automatico contiene un singolo file manifesto del prodotto, ma un manifesto del pacchetto per ogni impostazione locale. Il manifesto del pacchetto contiene aspetti specifici della localizzazione del pacchetto. Sono inclusi stringhe, contratti di licenza con l'utente finale e Language Pack.

 Per altre informazioni sui manifesti dei pacchetti, vedere [Procedura: Creare un manifesto del pacchetto.](../deployment/how-to-create-a-package-manifest.md)

## <a name="create-the-product-manifest"></a>Creare il manifesto del prodotto

#### <a name="to-create-the-product-manifest"></a>Per creare il manifesto del prodotto

1. Creare una directory per il pacchetto del programma di avvio automatico. Questo esempio Usa c:\package.

2. In Visual Studio creare un nuovo file XML denominato *product.xml* e salvarlo nella *cartella C:\package.*

3. Aggiungere il codice XML seguente per descrivere lo spazio dei nomi XML e il codice del prodotto per il pacchetto. Sostituire il codice prodotto con un identificatore univoco per il pacchetto.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Aggiungere CODICE XML per specificare che il pacchetto ha una dipendenza. Questo esempio usa una dipendenza da Microsoft Windows Installer 3.1.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Aggiungere XML per elencare tutti i file presenti nel pacchetto del programma di avvio automatico. In questo esempio viene utilizzato il nome file *del pacchettoCorePackage.msi*.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. Copiare o spostare *CorePackage.msi* file nella cartella *C:\package.*

7. Aggiungere codice XML per installare il pacchetto usando i comandi del programma di avvio automatico. Il programma di avvio automatico aggiunge automaticamente il flag **/qn** al file *.msi,* che verrà installato automaticamente. Se il file è un *.exe*, il programma di avvio automatico esegue *.exe* file usando la shell. Il codice XML seguente non mostra argomenti *CorePackage.msi*, ma è possibile inserire l'argomento della riga di comando nell'attributo `Arguments` .

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Aggiungere il codice XML seguente per verificare se questo pacchetto del programma di avvio automatico è installato. Sostituire il codice del prodotto con il GUID per il componente ridistribuibile.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Aggiungere codice XML per modificare il comportamento del programma di avvio automatico a seconda che il componente del programma di avvio automatico sia già installato. Se il componente è installato, il pacchetto del programma di avvio automatico non viene eseguito. Il codice XML seguente verifica se l'utente corrente è un amministratore perché questo componente richiede privilegi amministrativi.

    ```xml
    <InstallConditions>
        <BypassIf
           Property="IsMsiInstalled"
           Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
            Compare="ValueNotEqualTo" Value="True"
            String="NotAnAdmin"/>
    </InstallConditions>
    ```

10. Aggiungere codice XML per impostare i codici di uscita se l'installazione ha esito positivo e se è necessario un riavvio. Il codice XML seguente illustra i codici di uscita Fail e FailReboot, che indicano che il programma di avvio automatico non continuerà a installare i pacchetti.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Aggiungere il codice XML seguente per terminare la sezione per i comandi del programma di avvio automatico.

    ```xml
        </Command>
    </Commands>
    ```

12. Spostare la *cartella C:\package* nella directory del Visual Studio bootstrapper. Per Visual Studio 2010, si tratta della directory *\Programmi\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.*

## <a name="example"></a>Esempio
 Il manifesto del prodotto contiene istruzioni di installazione per i prerequisiti personalizzati.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Product
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  ProductCode="Custom.Bootstrapper.Package">

  <RelatedProducts>
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
  </RelatedProducts>

  <PackageFiles>
    <PackageFile Name="CorePackage.msi"/>
  </PackageFiles>

  <InstallChecks>
    <MsiProductCheck Product="IsMsiInstalled"
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
  </InstallChecks>

  <Commands>
    <Command PackageFile="CorePackage.msi" Arguments="">

      <InstallConditions>
        <BypassIf Property="IsMsiInstalled"
          Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
          Compare="ValueNotEqualTo" Value="True"
         String="NotAnAdmin"/>
      </InstallConditions>

      <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
      </ExitCodes>
    </Command>
  </Commands>
</Product>
```

## <a name="see-also"></a>Vedi anche
- [Informazioni di riferimento sullo schema di prodotti e pacchetti](../deployment/product-and-package-schema-reference.md)
---
title: 'Procedura: Creare un manifesto del prodotto | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68f3006104b50876f6d2716ff4eb1efe0a705284
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928366"
---
# <a name="how-to-create-a-product-manifest"></a>Procedura: Creare il manifesto di un prodotto
Per distribuire i prerequisiti per l'applicazione, è possibile creare un pacchetto di programma di avvio automatico. Un pacchetto bootstrapper contiene un file manifesto singolo prodotto ma un manifesto di pacchetto per ogni impostazione locale. Il manifesto del pacchetto contiene gli aspetti specifici della localizzazione del pacchetto. Si tratta di stringhe, contratti di licenza dell'utente finale e i language pack.

 Per altre informazioni sui manifesti di pacchetto, vedere [come: Creare un manifesto di pacchetto](../deployment/how-to-create-a-package-manifest.md).

## <a name="create-the-product-manifest"></a>Creare il manifesto del prodotto

#### <a name="to-create-the-product-manifest"></a>Per creare il manifesto del prodotto

1. Creare una directory per il pacchetto di programma di avvio automatico. Questo esempio Usa c:\package.

2. In Visual Studio, creare un nuovo file XML denominato *Product*e salvarlo per il *c:\package.* cartella.

3. Aggiungere il seguente codice XML per descrivere il codice di prodotto e lo spazio dei nomi XML per il pacchetto. Sostituire il codice prodotto con un identificatore univoco per il pacchetto.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Aggiungere codice XML per specificare che il pacchetto ha una dipendenza. Questo esempio Usa una dipendenza su Microsoft Windows Installer 3.1.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Aggiungere codice XML per elencare tutti i file nel pacchetto del programma di avvio automatico. Questo esempio viene usato il nome file del pacchetto *CorePackage. msi*.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. Copiare o spostare il *CorePackage. msi* del file per il *c:\package.* cartella.

7. Aggiungere codice XML per installare il pacchetto usando i comandi di avvio automatico. Il programma di bootstrap vengono aggiunti automaticamente il **/qn** flag per il *con estensione msi* file, che consente l'installazione invisibile all'utente. Se il file è un *.exe*, viene eseguito il programma di avvio di *.exe* file mediante la shell. Il codice XML seguente non mostra gli argomenti alcuna *CorePackage. msi*, ma è possibile inserire l'argomento della riga di comando nel `Arguments` attributo.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Aggiungere il codice XML seguente per verificare se è installato il pacchetto di programma di avvio automatico. Sostituire il codice prodotto con il GUID per il componente ridistribuibile.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Aggiungere codice XML per modificare il comportamento di avvio automatico a seconda se è già installato il componente di programma di avvio automatico. Se è installato il componente, il pacchetto di programma di avvio non eseguito. Il codice XML seguente controlla se l'utente corrente è un amministratore, poiché questo componente richiede privilegi amministrativi.

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

10. Aggiungere codice XML per impostare i codici di uscita se l'installazione ha esito positivo e, se è necessario riavviare il computer. Il codice XML seguente viene illustrato che l'esito negativo e FailReboot codici, che indicano che il programma di bootstrap non continuerà installazione dei pacchetti di uscita.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Aggiungere il codice XML seguente per terminare la sezione per i comandi di avvio automatico.

    ```xml
        </Command>
    </Commands>
    ```

12. Spostare il *c:\package.* cartella nella directory di avvio automatico di Visual Studio. Per Visual Studio 2010, questo è il *\Programmi\Microsoft Sdks\windows\v7.0A\Bootstrapper\Packages.* directory.

## <a name="example"></a>Esempio
 Il manifesto del prodotto contiene istruzioni di installazione di prerequisiti personalizzati.

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

## <a name="see-also"></a>Vedere anche
- [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)
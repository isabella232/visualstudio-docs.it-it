---
title: '&lt;Elemento &gt; Commands (programma di avvio automatico) | Microsoft Docs'
description: L'elemento Commands implementa i test negli elementi sottostanti InstallChecks e dichiara il pacchetto da installare se il ClickOnce del programma di avvio automatico ha esito negativo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: a343ae58306b85a7bd6dcb0332f1b69cbe5d04a7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104950"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Elemento Commands &gt; (programma di avvio automatico)
L'elemento implementa i test descritti dagli elementi sotto l'elemento e dichiara il pacchetto che il programma di avvio automatico deve `Commands` installare se il test ha esito `InstallChecks` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] negativo.

## <a name="syntax"></a>Sintassi

```xml
<Commands
    Reboot
>
    <Command
        PackageFile
        Arguments
        EstimatedInstallSeconds
        EstimatedDiskBytes
        EstimatedTempBytes
        Log
    >
        <InstallConditions>
            <BypassIf
                Property
                Compare
                Value
                Schedule
            />
            <FailIf
                Property
                Compare
                Value
                String
                Schedule
            />
        </InstallConditions>
        <ExitCodes>
            <ExitCode
                Value
                Result
                String
            />
        </ExitCodes>
    </Command>
</Commands>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `Commands`L'elemento è obbligatorio. L'elemento presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`Reboot`|Facoltativa. Determina se il sistema deve essere riavviato se uno dei pacchetti restituisce un codice di uscita per il riavvio. L'elenco seguente mostra i valori validi:<br /><br /> `Defer`. Il riavvio viene posticipato fino a un momento futuro.<br /><br /> `Immediate`. Causa un riavvio immediato se uno dei pacchetti ha restituito un codice di uscita di riavvio.<br /><br /> `None`. Fa sì che tutte le richieste di riavvio siano ignorate.<br /><br /> Il valore predefinito è `Immediate`.|

## <a name="command"></a>Comando
 L'elemento `Command` è un elemento figlio dell'elemento `Commands`. Un `Commands` elemento può avere uno o più elementi `Command` . L'elemento presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`PackageFile`|Obbligatorio. Il nome del pacchetto da installare deve essere una o più delle condizioni specificate da `InstallConditions` restituire false. Il pacchetto deve essere definito nello stesso file usando un `PackageFile` elemento .|
|`Arguments`|facoltativo. Set di argomenti della riga di comando da passare nel file del pacchetto.|
|`EstimatedInstallSeconds`|facoltativo. Tempo stimato, in secondi, necessario per installare il pacchetto. Questo valore determina le dimensioni dell'indicatore di stato che il programma di avvio automatico visualizza all'utente. Il valore predefinito è 0, nel qual caso non viene specificata alcuna stima temporale.|
|`EstimatedDiskBytes`|facoltativo. Quantità stimata di spazio su disco, in byte, che il pacchetto occuperà al termine dell'installazione. Questo valore viene usato nei requisiti di spazio su disco rigido che il programma di avvio automatico visualizza all'utente. Il valore predefinito è 0, nel qual caso il programma di avvio automatico non visualizza i requisiti di spazio su disco rigido.|
|`EstimatedTempBytes`|facoltativo. Quantità stimata di spazio su disco temporaneo, in byte, richiesta dal pacchetto.|
|`Log`|facoltativo. Percorso del file di log generato dal pacchetto, relativo alla directory radice del pacchetto.|

## <a name="installconditions"></a>InstallConditions
 `InstallConditions`L'elemento è figlio `Command` dell'elemento . Ogni `Command` elemento può avere al massimo un elemento `InstallConditions` . Se non `InstallConditions` esiste alcun elemento , il pacchetto specificato da verrà sempre `Condition` eseguito.

## <a name="bypassif"></a>BypassIf
 `BypassIf`L'elemento è figlio `InstallConditions` dell'elemento e descrive una condizione positiva in cui il comando non deve essere eseguito. Ogni `InstallConditions` elemento può avere zero o più `BypassIf` elementi.

 `BypassIf` ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà da testare. La proprietà deve essere stata definita in precedenza da un elemento figlio `InstallChecks` dell'elemento . Per altre informazioni, vedere [ \<InstallChecks> Elemento](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Obbligatorio. Tipo di confronto da eseguire. L'elenco seguente mostra i valori validi:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Obbligatorio. Valore da confrontare con la proprietà .|
|`Schedule`|facoltativo. Nome di un `Schedule` tag che definisce quando deve essere valutata questa regola.|

## <a name="failif"></a>FailIf
 L'elemento è un elemento figlio dell'elemento e descrive una condizione positiva in cui `FailIf` `InstallConditions` l'installazione deve essere interrotta. Ogni `InstallConditions` elemento può avere zero o più `FailIf` elementi.

 `FailIf` ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Property`|Obbligatorio. Nome della proprietà da testare. La proprietà deve essere stata definita in precedenza da un elemento figlio `InstallChecks` dell'elemento . Per altre informazioni, vedere [ \<InstallChecks> Elemento](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Obbligatorio. Tipo di confronto da eseguire. L'elenco seguente mostra i valori validi:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Obbligatorio. Valore da confrontare con la proprietà .|
|`String`|facoltativo. Testo da visualizzare all'utente in caso di errore.|
|`Schedule`|facoltativo. Nome di un `Schedule` tag che definisce quando deve essere valutata questa regola.|

## <a name="exitcodes"></a>ExitCodes
 `ExitCodes`L'elemento è figlio `Command` dell'elemento . L'elemento contiene uno o più elementi che determinano l'operazione che l'installazione deve eseguire in risposta `ExitCodes` a un codice di uscita da un `ExitCode` pacchetto. Sotto un elemento può essere `ExitCode` presente un elemento `Command` facoltativo. L'elemento `ExitCodes` non ha attributi.

## <a name="exitcode"></a>ExitCode
 `ExitCode`L'elemento è figlio `ExitCodes` dell'elemento . `ExitCode`L'elemento determina l'operazione che l'installazione deve eseguire in risposta a un codice di uscita da un pacchetto. `ExitCode` non contiene elementi figlio e dispone degli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Value`|Obbligatorio. Valore del codice di uscita a cui si `ExitCode` applica questo elemento.|
|`Result`|Obbligatorio. Modalità di reazione dell'installazione a questo codice di uscita. L'elenco seguente mostra i valori validi:<br /><br /> `Success`. Contrassegna il pacchetto come installato correttamente.<br /><br /> `SuccessReboot`. Contrassegna il pacchetto come installato correttamente e indica al sistema di riavviare.<br /><br /> `Fail`. Contrassegna il pacchetto come non riuscito.<br /><br /> `FailReboot`. Contrassegna il pacchetto come non riuscito e indica al sistema di riavviare.|
|`String`|facoltativo. Valore da visualizzare all'utente in risposta a questo codice di uscita.|
|`FormatMessageFromSystem`|facoltativo. Determina se usare il messaggio di errore fornito dal sistema corrispondente al codice di uscita oppure il valore fornito in `String` . I valori validi `true` sono , che indica l'utilizzo dell'errore fornito dal sistema, e , che indica `false` l'uso della stringa fornita da `String` . Il valore predefinito è `false`. Se questa proprietà è `false` , ma non è `String` impostata, verrà utilizzato l'errore fornito dal sistema.|

## <a name="example"></a>Esempio
 L'esempio di codice seguente definisce i comandi per l'installazione .NET Framework 2.0.

```xml
<Commands Reboot="Immediate">
    <Command PackageFile="instmsia.exe"
             Arguments= ' /q /c:"msiinst /delayrebootq"'
             EstimatedInstallSeconds="20" >
        <InstallConditions>
           <BypassIf Property="VersionNT" Compare="ValueExists"/>
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>
        </InstallConditions>
        <ExitCodes>
            <ExitCode Value="0" Result="SuccessReboot"/>
            <ExitCode Value="1641" Result="SuccessReboot"/>
            <ExitCode Value="3010" Result="SuccessReboot"/>
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
        </ExitCodes>
    </Command>
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"
             Arguments= '/quiet /norestart'
             EstimatedInstallSeconds="20" >
      <InstallConditions>
          <BypassIf Property="Version9x" Compare="ValueExists"/>
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>
      </InstallConditions>
      <ExitCodes>
          <ExitCode Value="0" Result="Success"/>
          <ExitCode Value="1641" Result="SuccessReboot"/>
          <ExitCode Value="3010" Result="SuccessReboot"/>
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
      </ExitCodes>
    </Command>
    <Command PackageFile="dotnetfx.exe"
         Arguments=' /q:a /c:"install /q /l"'
         EstimatedInstalledBytes="21000000"
         EstimatedInstallSeconds="300">

        <!-- These checks determine whether the package is to be installed -->
        <InstallConditions>
            <!-- Either of these properties indicates the .NET Framework is already installed -->
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>

            <!-- Block install if user does not have adminpermissions -->
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>

            <!-- Block install on Windows 95 -->
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>

            <!-- Block install on Windows 2000 SP 2 or less -->
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>

            <!-- Block install if Internet Explorer 5.01 or later is not present -->
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />

            <!-- Block install if the operating system does not support x86 -->
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />
       </InstallConditions>

        <ExitCodes>
            <ExitCode Value="0" Result="Success"/>
            <ExitCode Value="3010" Result="SuccessReboot"/>
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
        </ExitCodes>

    </Command>
</Commands>
```

## <a name="see-also"></a>Vedi anche
- [Informazioni di riferimento sullo schema di prodotti e pacchetti](../deployment/product-and-package-schema-reference.md)
- [\<InstallChecks> Elemento](../deployment/installchecks-element-bootstrapper.md)
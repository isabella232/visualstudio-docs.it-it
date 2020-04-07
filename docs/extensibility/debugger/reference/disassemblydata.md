---
title: Proprietà DisassemblyData . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737280"
---
# <a name="disassemblydata"></a>DisassemblyData
Viene descritta un'istruzione disassembly per l'ambiente di sviluppo integrato (IDE) da visualizzare.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Membri
`dwFields`\
La [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) DISASSEMBLY_STREAM_FIELDS costante che specifica quali campi vengono compilati.

`bstrAddress`\
L'indirizzo come offset da un punto di partenza (in genere l'inizio della funzione associata).

`bstrCodeBytes`\
Byte di codice per questa istruzione.

`bstrOpcode`\
Codice operativo per questa istruzione.

`bstrOperands`\
Gli operandi per questa istruzione.

`bstrSymbol`\
Il nome del simbolo, se presente, associato all'indirizzo (simbolo pubblico, etichetta e così via).

`uCodeLocationId`\
Identificatore della posizione del codice per questa riga disassemblata. Se l'indirizzo di contesto del codice di una riga è maggiore dell'indirizzo del contesto del codice di un'altra, anche l'identificatore di posizione del codice disassemblato della prima sarà maggiore dell'identificatore di posizione del codice della seconda.

`posBeg`\
Il [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che corrisponde alla posizione in un documento in cui iniziano i dati disassemblaggio.

`posEnd`\
Il [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che corrisponde alla posizione in un documento in cui terminano i dati disassembly.

`bstrDocumentUrl`\
Per i documenti di testo che `bstrDocumentUrl` possono essere rappresentati come nomi di file, il `file://file name`campo viene compilato con il nome del file in cui è possibile trovare l'origine, utilizzando il formato .

Per i documenti di testo che `bstrDocumentUrl` non possono essere rappresentati come nomi di file, è un identificatore univoco per il documento e il motore di debug deve implementare il [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) metodo.

Questo campo può inoltre contenere informazioni aggiuntive sui checksum. Per ulteriori informazioni, vedere Note.

`dwByteOffset`\
Il numero di byte dell'istruzione dall'inizio della riga di codice.

`dwFlags`\
Costante [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) che specifica quali flag sono attivi.

## <a name="remarks"></a>Osservazioni
Ogni `DisassemblyData` struttura descrive un'istruzione di disassemblaggio. Viene restituita una matrice di queste strutture dal metodo [Read.](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)

La struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) viene utilizzata solo per i documenti basati su testo. L'intervallo di codice sorgente per questa istruzione viene compilato solo per la `dwByteOffset == 0`prima istruzione generata da un'istruzione o una riga, ad esempio quando .

Per i documenti non testuali, è possibile ottenere un `bstrDocumentUrl` contesto di documento dal codice e il campo deve essere un valore null. Se `bstrDocumentUrl` il campo è `bstrDocumentUrl` uguale al `DisassemblyData` campo nell'elemento `bstrDocumentUrl` della matrice precedente, impostare il su un valore null.

Se `dwFlags` nel campo `DF_DOCUMENT_CHECKSUM` è impostato il flag, le informazioni aggiuntive `bstrDocumentUrl` sul checksum seguono la stringa a cui punta il campo. In particolare, dopo il terminatore di stringa null, segue un GUID che identifica l'algoritmo di checksum che è a sua volta seguito da un valore di 4 byte che indica il numero di byte nel checksum e che a sua volta è seguito dai byte di checksum. Vedere l'esempio in questo argomento su come codificare e decodificare questo campo in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].

## <a name="example"></a>Esempio
Il `bstrDocumentUrl` campo può contenere informazioni aggiuntive `DF_DOCUMENT_CHECKSUM` diverse da una stringa se il flag è impostato. Il processo di creazione e lettura [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]di questa stringa codificata è semplice in . Tuttavia, [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]in , è un'altra questione. Per coloro che sono curiosi, l'esempio seguente [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] mostra un modo per creare [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]la stringa codificata da e un modo per decodificare la stringa codificata in .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Leggere](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

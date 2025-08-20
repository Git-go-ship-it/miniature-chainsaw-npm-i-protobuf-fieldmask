 # protobuf-fieldmask

[![npm version](http://img.shields.io/npm/v/protobuf-fieldmask.svg)](https://npmjs.org/package/protobuf-fieldmask)
[![npm downloads](https://img.shields.io/npm/dm/protobuf-fieldmask.svg)](https://npmjs.org/package/protobuf-fieldmask)
![](https://github.com/kibertoad/protobuf-fieldmask/workflows/unit-tests/badge.svg)
[![Coverage Status](https://coveralls.io/repos/kibertoad/protobuf-fieldmask/badge.svg?branch=master)](https://coveralls.io/r/kibertoad/protobuf-fieldmask?branch=master)

Library for generating and applying protobuf [FieldMask](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/field-mask)

## Usage

### generateFieldMask
```
/**
 * Generates field mask that includes all non-function own properties on specified object
 * @param {*} object - object to generate field mask from
 * @returns {string[]} - generated field mask
 */
function generateFieldMask(object)
```

The name of the properties containing `.` or `\` characters are escaped. 

For an example, running this function with this input:
```
{
  f: {
    a: 22,
    b: {
      d: 1
    },
    'b.d': 33,
    'x\\y': 44
  }
}
```

generates this output:
```
['f.a', 'f.b.d', 'f.b\\.d', "f.x\\\\y"]
```

### applyFieldMask
```
/**
 * Creates a new object that copies fields present in field mask from specified source object
 * @param {*} sourceObject - object to apply field mask to
 * @param {string[]} fieldMask
 * @returns {*} - new object created by applying field mask on source object or original entity if source is not an object
 */
function applyFieldMask(sourceObject, fieldMask)
```

Respects the escaping of the property names in the `fieldMask`.

For an example, running this function with this input:
```
{
  f: {
    a: 22,
    b: {
      d: 1,
      x: 2
    },
    'b.d': 33,
    y: 13
  },
  z: 8
},
['f.a', 'f.b.d', 'f.b\\.d']
```

generates this output:
```
{
  f: {
    a: 22,
    b: {
      d: 1
    },
    'b.d': 33
  }
}
```

Special thanks to Jorge Yero Salazar for providing TS typings!
แถบด้านข้างแพ็คเกจ
ติดตั้ง
npm i protobuf-fieldmask

ที่เก็บข้อมูล
github.com/kibertoad/โปรโตบัฟ-ฟิลด์มาสก์

หน้าแรก
github.com/kibertoad/โปรโตบัฟ-ฟิลด์มาสก์

ดาวน์โหลดรายสัปดาห์
14,574

เวอร์ชัน
2.0.0

ใบอนุญาต
เอ็มไอที

ขนาดเมื่อแกะบรรจุภัณฑ์
8.8 กิโลไบต์

ไฟล์ทั้งหมด
7

ปัญหา
0

คำขอดึง
0

เผยแพร่ครั้งสุดท้าย
2 ปีที่แล้ว

ผู้ร่วมมือ
คางคกคิเบอร์
ลองใช้ RunKit
รายงานมัลแวร์
ส่วนท้าย
สนับสนุน
ช่วย
คำแนะนำ
สถานะ
ติดต่อ npm
บริษัท
เกี่ยวกับ
บล็อก
กด
ข้อกำหนดและนโยบาย
นโยบาย
เงื่อนไขการใช้งาน
จรรยาบรรณในการประพฤติตน
ความเป็นส่วนตัว


## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |

## Reporting a Vulnerability

Use this section to tell people how to report a vulnerability.

Tell them where to go, how often they can expect to get an update on a
reported vulnerability, what to expect if the vulnerability is accepted or
declined, etc.

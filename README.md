# Proje Kaynakları

- Araç verileri için API:
- https://publ1ic.opendatasoft.com/explore/dataset/all-vehicles-model/api/?sort=scharger

- Fotoğraf üretmek için API:
- https://docs.imagin.studio/guides/getting-images/embedding-in-your-website
- https://cdn.imagin.studio/getImage?customer=hrjavascript-mastery&make=BMW&modelFamily=m4

# TS ile React Yazılırken Dikkat

- Tip tanımlanabilecek her değişkenin / fonksiyonun tipi tanımlanmalı.
- Tipi tanımlanmamış bir değişken bile bırakılmamalı
- Oto tip algılama özelliği olabiilidğince az kullanılmalı, mümkünse hiç kullanılmamalı

## useState

- useState kullanırken state'ini tutucağımız değişkenin tipini useState'e generic olarak gödeririz

- evet useState oto olarak algılayabilir ama yukarıdada dediğiimiz gibi mümkünse o özelliği hiç kullanmamalıyız

## Prop Tipi

- Bir bileşenin aldığı prop'lardan ziyade artık prop'ları tipinide tanımlamak zorundayız.

- Ve bu bilşeni kullanırken tanımladığımız tipteki propları göndermezsek hata alırız

```js
import React, { FC } from "react";

// Component'ın aldığı prop'larının tipini tanımlama
type Props = {
  text: string,
};

// Component tipi tanımla - RETURN TİPİ OTO ALGILAMA
const Button = ({ text }: Props) => {
  return <button>{text}</button>;
};

// Component tipi tanımla - RETURN TİPİ AYRI PROP TİPİ AYRI
const Input = ({ text }: Props): JSX.Element => {
  return <input />;
};

// Component tipi tanımla - REACT.FC Yöntemi
const Select: FC<Props> = ({ text }) => {
  return <select />;
};

const Form: FC = () => {
  // form gönderilince
  const handleSubmit = (e: FormEvent<HTMLFormElement>) => {
    e.preventDefault();
  };

  // butona tıklanınca
  const handleClick = (e: MouseEvent<HTMLButtonElement>) => {};

  // input değişince
  const handleChange = (e: ChangeEvent<HTMLInputElement>) => {
    e.target.value;
  };

  return (
    <form onSubmit={handleSubmit}>
      <input onChange={handleChange} type="text" placeholder="İsminiz" />

      <button onClick={handleClick}>gönder</button>
    </form>
  );
};
```

# Proje Yayınlama Adımları

1. Projenizi Hazırlayın
2. Alan Adı (Domain) && SSL Kirala
3. Hosting Platformu Seç
4. Projeyi hosting ile yayınla (deploy etme)
5. DNS ayarlarını yap
6. Web sitesini kontrol et
7. SEO Kontrolü / İyileştirmesi

# Hosting

1. Modern Hosting Çözümleri

- Projeyi github resposu üzerinden tek tıkla yayınlayabiliyoruz.
- Vercel, Netlify, Cloudflate Pages, Github Pages

### Vercel

- Modern framewrokler için tam uyumlu
- Ücretsiz planı küçük projeler için ideal
- Otomatik SSL, CDN, CI/CD (Sürekli Dağıtım)

2. Geleneksel Hosting Çözümleri

- Kendi sunucumuzu kiralayıp her şeyi manuel olarak yapıyoruz.

- VPS (Virtual Private Server): Digital Ocean, Linode, Vultr
- AWS S3
- Firebase Hosting

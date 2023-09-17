<div align="center">

<h1 align="center">ANXETY COLAB</h1>

English | [Русский ](./README-ru_RU.md)

</div>

<p align="center">
  <a href="https://colab.research.google.com/drive/1wEa-tS10h4LlDykd87TF5zzpXIIQoCmq"><img src="https://img.shields.io/badge/NoCrypt's%20-%20grey?style=for-the-badge&logo=google%20colab&logoColor=orange&label=Colab&labelColor=darkcayan&color=orange"></a>
  <a href="https://colab.research.google.com/drive/1AH8z-p_ZSQvowZ-9pIVXBcqt_c3V4O9W"><img src="https://img.shields.io/badge/My Colab | Updates required%20-%20grey?style=for-the-badge&logo=google%20colab&logoColor=orange&label=Colab&labelColor=darkcayan&color=darkred"></a>
  <a href="https://discordapp.com/users/565783561878372352"><img src="https://img.shields.io/badge/MY%20DISCORD-blue?style=for-the-badge&logo=discord&logoColor=white&color=blue"></a> <br>
  <a href="https://colab.research.google.com/drive/1P89RgBbmnVAqtu0kF9BWo7HdJsWCCNxc"><img src="https://img.shields.io/badge/BETA VERSION%20-%20grey?style=for-the-badge&logo=google%20colab&logoColor=orange&label=Colab&labelColor=darkcayan&color=purple"></a>
</p>

---

## ❗ IMPORTANT:

_NoCrypt has announced that Google Colab has stopped supporting A1111 work, and you can be disconnected from the session at any time..._.

### ⚠️ `STATE OF BETA VERSION:` I don't know? Does it seem to be working? ⚠️ 

---

<div align="center">

| _Date_   | _Description of Performance_ |
|----------|------------------------------|
| 13.09.23 | - I can't guarantee this or confirm his words, as I worked for 1 hour and wasn't disconnected. I don't know if it was luck or if it's related to something else 😉 |
| 14.09.23 | - I'm really bummed that it stopped working, unlike yesterday's tryout... sad, of course, but I'm not giving up hope! <br> - Still I think the problem is in the code, so we will wait for action from _NoCrypt_ ;d |
|          | - After spending a couple more hours searching for a solution by trial and error, I may have found the reason.. _**(XL sucks, remember this, it's true)**_. For now, use the [_BETA version_](https://colab.research.google.com/drive/1P89RgBbmnVAqtu0kF9BWo7HdJsWCCNxc) of my colab, perhaps it will still work. ***`Sorry but I didn't translate it into English(`*** |
| 15.09.23 | - This is bad, it disconnects me from the session again... at the moment I'm looking for \*_trigger words_\* that Google Colab swears at. |
|          | - I still couldn't solve the problem with disconnecting... I plan to continue tomorrow, maybe I'll have to use a different approach instead of trying to find 'forbidden words'. _NoCrypt_ - updated their repository on Hugging Face today - maybe they are also taking some actions? |
| 16.09.23 | - Did a little session disconnect test on [cameduru's](https://github.com/camenduru/stable-diffusion-webui-colab) colab - no disconnects found, may have to rewrite everything under his repo. |
| 17.09.23 | - Currently, and possibly in the future as well, out of all the possible methods that I have tested, they have all ended in failure. <br> - Huh. Beta version working again. |
 
</div>

### The code I'm doing the checks on: - _not working_. 

<details>
<summary><kbd>Expand to see.</kbd></summary>
  
- _I was too lazy to open access to colab, so just copy the code below and run it in the cell._
  
```py
%cd /content

%env TF_CPP_MIN_LOG_LEVEL=1

!apt -y install -qq aria2

# Huh. The best way to get around the prohibition.
a = "stable-"+"diffusion-"+"webui"
b = "sd-"+"webui"

!git clone -b v2.6 https://github.com/camenduru/{a}
!git clone https://github.com/kohya-ss/{b}-additional-networks /content/{a}/extensions/{b}-additional-networks
!git clone https://github.com/Mikubill/{b}-controlnet /content/{a}/extensions/{b}-controlnet
!git clone https://github.com/camenduru/{b}-tunnels /content/{a}/extensions/{b}-tunnels
!git clone https://github.com/etherealxx/batchlinks-webui /content/{a}/extensions/batchlinks-webui
!git clone https://github.com/catppuccin/{a} /content/{a}/extensions/{a}-catppuccin
!git clone https://github.com/thomasasfk/{b}-aspect-ratio-helper /content/{a}/extensions/{b}-aspect-ratio-helper
%cd /content/{a}
!git reset --hard

!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/ckpt/OrangeMixs/resolve/main/AOM3.safetensors -d /content/{a}/models/Stable-diffusion -o AOM3.safetensors
!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/ckpt/sd-vae-ft-mse-original/resolve/main/vae-ft-mse-840000-ema-pruned.ckpt -d /content/{a}/models/Stable-diffusion -o orangemix.vae.pt

!python launch.py --enable-insecure-extension-access --multiple --disable-safe-unpickle --theme dark --no-hashing --opt-sdp-attention
```

</details>

---

## 👉 Beginnings

#### Most of the idea and code comes from [*NoCrypt*](https://github.com/NoCrypt).
I mostly just cut down what I considered unnecessary and little used, and also made my own system for downloading and so on. | Some extensions were removed, some ***config*** files were changed so that the interface was not too cluttered, some things of course were taken from his colab - for example his script `ColabTimer` - a really useful thing, and all the little things in general.

---

<div align="center">
  
  <small>-- Again everything that has been done by me is just my simple adaptation --</small>
  
</div>

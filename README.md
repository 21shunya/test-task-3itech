# Тестовое задание

## 1. Верстка
### Задача: дополнить scss правила так, чтобы представленная html разметка приобрела вид как на картинке.

![пример](https://raw.githubusercontent.com/3itech-frontend/interview-tasks/main/example.png)

```html
<div class='dialog-container'>
    <div class='dialog'>
        <div class='dialog__header'>
            <div class='dialog__header-title-container'>
                <div class='dialog__header-title'>
                    Ссъешь ещё этих мягких французских булок, да выпей чаю
                </div>
                <div class='dialog__header-subtitle'>
                    Съешь ещё этих мягких французских булок, да выпей чаю
                </div>
            </div>
            <button class='dialog__header-button'>
                Кнопка закрытия
            </button>
        </div>
        <div class='dialog__content'>
            <div class='dialog__content-block dialog__content-block_left'>
                Left
            </div>
            <div class='dialog__content-block dialog__content-block_right'>
                <div class='content'>
                    <span>Top</span>
                    <span>Center</span>
                    <span>Bottom</span>
                </div>
            </div>
        </div>
        <div class='dialog__footer'>
            Ссъешь ещё этих мягких французских булок, да выпей чаю<br />
            ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789<br />
            Ссъешь ещё этих мягких французских булок, да выпей чаю
        </div>
    </div>
</div>
```

```SCSS
.dialog-container {
    position: fixed;
    left: 0;
    top: 0;
    width: 100vw;
    height: 100vh;
    background-color: #777;
}

.dialog {
    background-color: #fff;
    max-height: 500px;
    max-width: 350px;

    &__header {
        background-color: #ddd;
    }

    &__header-title-container {
    }

    &__header-title {
    }

    &__header-button {
    }

    &__content {
    }

    &__content-block {
        &_left {
            width: 30%;
            border-right: 1px solid #ccc;
        }

        &_right {
            width: 70%;
        }
    }

    &__footer {
        background-color: #ddd;
    }
}

.content {
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    height: 500px;
    width: 100%;
}
```

## 2. JS
### Задача: написать функцию `decode` в том же стиле, что и функция `encode` (вытянутой в цепочку) и узнать значение переменной `input`

```javascript
const encode = input => [...input]
    .map((x, i) => [x.charCodeAt(0), i])
    .sort()
    .flatMap(x => x)
    .join('.')
    .match(/./g)
    .flatMap((x, i) => new Array(x == '.' ? 1 : 2 + x * 2).fill((1 + i) % 2))
    .join('')
    .replace(/(([01])\2*)/g, x => `${(+x ? '.' : '-')}${x.length}`)
```

#### `encode(input)`:
```
.10-12.1-4.2-1.10-12.1-4.2-2.1-10.12-1.4-2.10-1.10-12.1-4.2-18.1-10.12-1.4-4.6-1.10-12.1-4.4-16.1-10.12-1.4-6.6-1.10-12.1-4.6-14.1-10.12-1.4-8.4-1.10-12.1-4.8-14.1-10.12-1.4-10.1-10.12-1.4-10.2-1.10-12.1-4.10-10.1-10.12-1.4-10.18-1.10-12.1-4.12-6.1-10.12-1.4-12.14-1.10-12.1-4.14-4.1-10.12-1.4-14.12-1.10-12.1-4.14-20.1-10.12-1.4-16.8-1.10-12.1-4.16-16.1-10.12-1.4-18.1-10.12-1.6-1.10-12.1-6.6-1.10-12.1-6.16-1.10-12.1-8.4-1.10-12.1-8.14-1.10-12.1-10.2-1.10-12.1-10.10-1.10-12.1-10.20-1.10-12.1-12.8-1.10-12.1-12.16-1.10-12.1-14.1-10.12-1.14-6.1-10.12-1.14-14.1-10.12-1.16-2.1-10.12-1.16-10.1-10.12-1.16-18.1-10.12-1.18-6.1-10.12-1.18-14.1-10.12-1.20-4.1-10.12-1.20-12.1-10.14-1.2-1.10-14.1-4.2-6.1-10.14-1.4-2.14-1.10-14.1-4.4-2.1-10.14-1.4-4.12-1.10-14.1-4.6-1.10-14.1-4.6-2.1-10.14-1.4-6.10-1.10-14.1-4.6-20.1-10.14-1.4-8.10-1.10-14.1-4.8-18.1-10.14-1.4-10.6-1.10-14.1-4.10-14.1-10.14-1.4-12.2-1.10-14.1-4.12-10.1-10.14-1.4-12.18-1.10-14.1-4.14-1.10-14.1-4.14-8.1-10.14-1.4-14.16-1.10-14.1-4.16-4.1-10.14-1.4-16.12-1.10-14.1-4.16-20.1-10.14-1.6-2.1-10.14-1.6-12.1-10.14-1.6-20.1-10.14-1.8-10.1-10.14-1.8-18.1-10.14-1.10-1.10-14.1-10.6-1.10-14.1-10.16-1.10-14.1-12.4-1.10-14.1-12.12-1.10-14.1-12.20-1.10-14.1-14.10-1.10-14.1-14.18-1.10-14.1-16.6-1.10-14.1-16.14-1.10-14.1-18.1-10.14-1.18-2.1-10.14-1.18-10.1-10.14-1.18-18.1-10.14-1.20-8.1-10.14-1.20-16.1-10.18-1.4-8.8-1.10-18.1-4.14-2.1-10.20-1.4-2.4-1.10-20.1-4.2-16.1-10.20-1.4-4.8-1.10-20.1-4.4-14.1-10.20-1.4-4.18-1.10-20.1-4.6-4.1-10.20-1.4-6.16-1.10-20.1-4.8-1.10-20.1-4.8-2.1-10.20-1.4-8.6-1.10-20.1-4.8-12.1-10.20-1.4-10.8-1.10-20.1-4.10-20.1-10.20-1.4-12.16-1.10-20.1-4.14-6.1-10.20-1.4-14.18-1.10-20.1-4.16-6.1-10.20-1.4-16.18-1.10-20.1-4.18-2.1-10.20-1.6-4.1-10.20-1.6-8.1-10.20-1.6-14.1-10.20-1.8-6.1-10.20-1.8-12.1-10.20-1.8-20.1-10.20-1.10-12.1-10.20-1.10-18.1-10.20-1.12-10.1-10.20-1.14-2.1-10.20-1.14-8.1-10.20-1.14-16.1-10.20-1.16-1.10-20.1-16.12-1.10-20.1-16.20-1.10-20.1-18.16-1.10-20.1-18.20-1.10-20.1-20.6-1.10-20.1-20.18-1.12-2.1-4.10-16.1-12.2-1.4-12.20-1.12-2.1-4.16-1.12-2.1-6.10-1.12-2.1-8.1-12.2-1.8-2.1-12.2-1.8-8.1-12.2-1.8-16.1-12.2-1.10-8.1-12.2-1.12-18.1-12.2-1.20-20.1-12.6-1.4-1.12-6.1-4.2-8.1-12.6-1.4-2.20-1.12-6.1-4.4-4.1-12.6-1.4-6.8-1.12-6.1-4.6-12.1-12.6-1.4-8.16-1.12-6.1-4.10-12.1-12.6-1.4-12.1-12.6-1.4-12.4-1.12-6.1-4.16-2.1-12.6-1.4-18.4-1.12-6.1-4.20-1.12-6.1-6.18-1.12-6.1-10.4-1.12-6.1-12.1-12.6-1.12-2.1-12.6-1.12-6.1-12.6-1.12-14.1-12.6-1.14-20.1-12.6-1.16-4.1-12.6-1.16-8.1-12.6-1.18-4.1-12.6-1.18-8.1-12.6-1.20-1.12-6.1-20.10-1.12-6.1-20.14-1.12-10.1-4.4-1.12-10.1-4.4-10.1-12.10-1.4-8.20-1.12-10.1-4.10-4.1-12.10-1.4-12.8-1.12-10.1-4.12-12.1-12.10-1.4-14.14-1.12-10.1-4.16-14.1-12.10-1.14-12.1-12.10-1.18-12.1-12.10-1.20-2.1-12.14-1.4-2.12-1.12-14.1-4.4-20.1-12.14-1.4-6.18-1.12-14.1-4.14-10.1-12.14-1.4-16.10-1.12-14.1-10.14-1.12-14.1-14.4-1.12-14.1-16.16
```

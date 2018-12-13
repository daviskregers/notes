# Bind click to document

```javascript
document.addEventListener('click', (event) => {
    if (event.target.matches('a.some-class')) {
        event.preventDefault();
        alert('do something!')
    }
}, false);
```
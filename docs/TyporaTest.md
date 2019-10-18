---
typora-copy-images-to: images
---

Typora that is a huge margin. kljfljfljsldfkjsdlf lskjdfls lskjd fl lskdjf l lkjsdf ll lksdjf lll sdflkl lskdjf ll sdlfkj llsjd fllksjdf llksdjf lskdjf lksdjf llskdj flslskdjf lslskjd fpwuerp wriu wsdjf lsz,mnvcnv ,xnv ,xc

<img src="images/Screenshot 2019-10-17 at 8.32.38 PM.png" alt="GitHub Commit Chart" style="zoom:150%;" />

## There must be a better way to insert images!

![](images/Screenshot 2019-10-12 at 1.00.53 PM.png)

This is a quick bit of code:

```javascript
class GoogleAuth extends React.Component {
  componentDidMount() {
    window.gapi.load("client:auth2", () => {
      window.gapi.client
        .init({
          clientId:
            "318802615607-3l2k61n5spk3n7u6b2mb49geeqi2ueng.apps.googleusercontent.com",
          scope: "email"
        })
        .then(() => {
          this.auth = window.gapi.auth2.getAuthInstance();
          this.onAuthChange(this.auth.isSignedIn.get());
          this.auth.isSignedIn.listen(this.onAuthChange);
        });
    });
  }
```

Have some tasks to do...

- [ ] do this
- [x] and this
- [ ] not this

Now what ?


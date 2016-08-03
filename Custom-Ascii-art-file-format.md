As of [#298](https://github.com/dylanaraps/neofetch/pull/298) neofetch now uses the distro ascii
format for custom ascii files.

Here's an example:

```sh
"\
${c1}                 ;\'-.
     \`;-._        )  \'---.._
       >  \`-.__.-\'          \`'\'__
      /_.-\'-._         _,  ${c2} ^${c1} ---)
      \`       \`\'------/_.\'----\`\`\`
"
```

Rules:

- The ascii art must be kept inside quotes like above.
    - `"\` as the opening
    - `"` as the ending
- You have to escape these characters:
    - `\`, `'`, `"`, `` ` `` 
- You can use `${c1}` to `${c6}`to color the ascii.
- You can pass the flag `--ascii_colors 1 2 3 4 5 6` to set the colors.
    - This changes the values of `${c1}` to `${c6}`
    - `--ascii_colors 2 5 6 1` changes `${c1}` to `Green`, `${c2}` to `Magenta` and etc.


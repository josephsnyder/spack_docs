#SPACK Infrastructure

```dot
digraph g {
  rankdir=LR;
  compound=true;
  subgraph cluster_AWS {
    label="Amazon Web Services";
    graph[style=dotted];
    subgraph cluster_EC2 {
      label="EC2";
      graph[style=dotted];
      subgraph cluster_arm {
        label="ARM Pods";
        graph[style=dotted];
        small;
        medium;
        large;
        xlarge;
        huge;
      };
      subgraph cluster_x {
        label="x86 Pods";
        graph[style=dotted];
        a_small[label="Small"];
        a_medium[label="Medium"];
        a_large[label="Large"];
        a_xlarge[label="Xlarge"];
        a_huge[label="huge"];
      };
    };
  };
  GitHub;
  Spackbot;
  Spackbot->GitHub[label="Listens for Comments"];
  GitHub->small[lhead=cluster_AWS, label="Pushes Jobs"];
}
```
##Spackbot

Spackbot is a GitHub service account which is able to execute certain tasks.

##AWS

The AWS section of the CI infrastructure contains a Kubernetes instance which
allows for the on-demand creation of testing instances.  The instance size that
is used is determined by the tag given to the job in the GitLab CI YAML file.


```dot
digraph g {
  rankdir=LR
  compound=true;
  subgraph cluster_EC2 {
    label="EC2";
    graph[style=dotted];
    subgraph cluster_arm {
      label="ARM";
      graph[style=dotted];
      small;
      medium;
      large;
      xlarge;
      huge;
    };
    subgraph cluster_x {
      label="x86";
      graph[style=dotted];
      a_small[label="Small"];
      a_medium[label="Medium"];
      a_large[label="Large"];
      a_xlarge[label="Xlarge"];
      a_huge[label="huge"];
    };
  };
}
```
##GitHub

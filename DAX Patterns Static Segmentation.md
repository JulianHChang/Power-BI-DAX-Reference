# Static Segmentation
[Link](https://www.daxpatterns.com/static-segmentation/)


Basic Pattern Example


[Price Range] =
CALCULATE (
    VALUES ( Ranges[Price Range] ),
    FILTER (
        Ranges,
        Sales[Price] >= Ranges[Min Price] 
        && Sales[Price] < Ranges[Max Price] 
    )
)


Complete Pattern

[Segment Name] =
CALCULATE (
    VALUES ( Segments[Segment Name] ),
    FILTER (
        Segments,
        Sales[Value] >= Segments[Min Value] 
        && Sales[Value] < Segments[Max Value] 
    )
)


[Segment Name] =
IFERROR (
    CALCULATE (
        VALUES ( Segments[Segment Name] ),
        FILTER (
            Segments,
            Sales[Value] >= Segments[Min Value] 
            && Sales[Value] < Segments[Max Value] 
        )
    ),
    "<config error>"
)


[Segment Position] =
IFERROR (
    CALCULATE (
        VALUES ( Segments[Segment Position] ),
        FILTER (
            Segments,
            Sales[Value] >= Segments[Min Value] 
            && Sales[Value] < Segments[Max Value] 
        )
    ),
    -1 
)